---
type: design-doc
project: second-brain-framework
date: 2026-07-03
status: architecture locked, build in progress
---

# Design & Build Document: 2nd Brain Framework for AI Agents

## 1. Purpose & Goal

Build a teachable framework/demo for using a "2nd brain" (persistent,
external memory) to get better multi-session results from Claude — and,
by extension, other AI agents.

**Audience:** both individuals and teams. Framework should be usable by
non-technical people day-to-day, while remaining extensible for technical
users who want to go further (e.g. add RAG/vector search, extend to
autonomous agents).

**Scope decision:** the core deliverable targets Claude specifically.
Extending the pattern to other/autonomous agents is left as a natural
extension technical users can figure out themselves — not part of the
core build.

## 2. Why This Approach (Reasoning Trail)

### 2.1 The underlying problem
A model's context window is short-term working memory that resets between
sessions. Without an external system, every new session starts cold —
the user re-explains project state, org context, and preferences every
time. The "2nd brain" is long-term memory living outside the model, with
relevant pieces loaded back into context when needed.

### 2.2 Memory isn't one thing — three types identified
Early in the discussion we identified that the use cases the user was
already running (business/org context, personal communication style,
research capture, customer data) aren't the same *kind* of memory, and
treating them identically is why vaults tend to rot:

| Type | Examples | Shape | Usage pattern |
|---|---|---|---|
| Entity/reference data | Org structure, customers | Structured, relational | Looked up on demand |
| Persistent profile/instruction | Communication style | Static, rarely changes | Applied to everything, every session |
| Episodic + semantic knowledge | Research | Narrative → distilled → linked | Accumulated, cross-referenced over time |

### 2.3 The always-load vs. on-demand classifier
This became the single most important reusable concept in the whole
framework — a generalization of the communication-style question ("where
does this live?") into a rule anyone can apply to *any* new content type:

> **Does this need to shape behavior even when it's not the explicit topic
> of the conversation?**
> - Yes → **always-load** (a lens: communication style, standing constraints)
> - No → **on-demand** (a fact: project state, an entity, a research note)

Failure modes on both sides: misclassifying a lens as on-demand means it
gets skipped constantly (this is what happened to the user's original
communication-style setup, which lived somewhere disconnected from the
vault). Misclassifying a fact as always-load bloats every session with
irrelevant content.

A specific edge case worth keeping as a teaching example: **standing
instructions can hide inside on-demand data.** E.g., a team entity note
that includes "always flag security implications for this team's
projects" — the note as a whole is on-demand, but that one line behaves
like always-load whenever the note *is* pulled in. Seeded in the template
as `04-entities/teams/platform-engineering.md`.

### 2.4 Where communication style should live
Discussed vault file vs. Claude's native platform settings (Claude.ai
preferences). Decision: **the vault file is the taught pattern**, because
it's portable (travels to teammates, other tools, other agents) and
auditable as real content. Native settings are a legitimate *supplement*
(catch Claude before the vault loads) but not a replacement — the native
setting should just point back to the vault file rather than duplicating it.

### 2.5 Tooling choice: Obsidian + MCP over vector/RAG
Considered file-based (markdown/JSON), MCP-based, and vector DB/RAG
approaches. Decision: **Obsidian + Obsidian MCP server**, deliberately
skipping vector search for v1.

Reasoning:
- Obsidian gives non-technical users a real GUI (backlinks, graph view)
  with zero code required to *use* the vault day-to-day.
- MCP lets Claude read/write natively instead of copy-pasting context.
- For personal/team-scale vaults, structured folders + a good index note
  are more transparent and easier to explain than semantic search.
- Vector/RAG is flagged as a natural "next step" for technical users, not
  part of the core teaching path.

### 2.6 Opinionated pattern, not a toolkit
Decision: ship **one** best-practice pattern rather than 2–3 side-by-side
options. Reasoning: easier to teach, easier to fork, and technical users
capable of wanting alternatives are also capable of adapting a single
clear pattern on their own.

### 2.7 Flagship demo: session continuity
Of the candidate use cases (session continuity, decision logging,
cross-project reuse), **session continuity** was chosen as the flagship
because it's the most relatable pain point and functions as a superset —
solving it well requires a decision log and reusable context to already
exist, so the other use cases show up as supporting mechanics rather than
separate demos.

### 2.8 Deliverable sequencing
Three target formats identified: GitHub template repo, workshop/course
module, blog-style writeup. Decision: **build in that order** — repo
first, since the workshop module and writeup can both reuse it rather
than duplicating work.

## 3. Architecture (as built)

```
CLAUDE.md              — session ritual instructions + classifier (read first, always)
_index.md              — map of content (read second, always)
00-inbox/              — unsorted capture, triaged manually
01-projects/           — active project state (on-demand)
02-context/
  communication-style.md  — ALWAYS-LOAD standing instruction
  (other notes)            — decisions, reusable patterns (on-demand)
03-sessions/           — dated session logs (on-demand; latest read when a project is active)
04-entities/
  people/ teams/ customers/  — structured YAML frontmatter, queryable like a lightweight DB
05-research/           — topic-organized: source + own-words summary + links
demo/before-after.md   — flagship demo transcript
README.md              — setup instructions
```

**The core mechanic** is a two-part ritual enforced by `CLAUDE.md`:
- **Session start:** read always-load content, then map, then relevant
  on-demand content (active project + latest session log + any entities
  mentioned) — before responding.
- **Session end:** write back what happened, decisions **and why**, open
  threads, and next steps to a new session-log entry; update the project
  note if state materially changed.

The "why" capture in session logs was called out specifically as the
part that's normally lost and is the actual value-add over a plain
to-do list or status doc.

## 4. What's Built So Far

- [x] Full folder structure scaffolded
- [x] `CLAUDE.md` with ritual instructions + classifier
- [x] `_index.md`
- [x] Seeded examples: communication style, one project note, one session
      log, one person/team/customer entity, one research note
- [x] `README.md` with setup instructions
- [x] `demo/before-after.md` flagship transcript
- [x] Zip packaged for download

## 5. Open Threads / Not Yet Resolved

- **Shared/team vault mechanics** — how this holds up when multiple
  people write session logs against the same vault (conflict handling,
  attribution of who wrote what) has not been designed yet.
- **Project note bloat** — no defined process yet for when a project note
  gets too large/stale and needs to be split or archived.
- **Live-testing the ritual** — `CLAUDE.md` wording has not yet been
  tested against a real Obsidian + MCP connection; wording may need to
  change based on observed behavior.
- **Workshop module** — not started; depends on the repo being validated
  first.
- **Blog/writeup** — not started; lowest priority of the three formats.

## 6. Next Steps

1. Move the repo into a real git-tracked folder (recommended: via Claude
   Code, not this chat — see rationale below).
2. Connect to a real Obsidian vault + MCP server and run an actual
   session to test whether `CLAUDE.md`'s instructions produce the
   intended behavior.
3. Iterate on `CLAUDE.md` wording based on observed gaps.
4. Resolve the shared-vault question if team use is a near-term priority.
5. Once validated, extract the workshop module from the working repo.
6. Write the blog/writeup last, reusing the before/after demo and design
   rationale already captured here.

## 7. Why the Handoff to Claude Code

This chat is well-suited to design/brainstorming (what we just did) but
can't test the MCP ritual live — there's no access here to the user's
actual Obsidian vault or MCP connection. Claude Code runs locally, so it
can `git init`, connect to the real vault, and iterate on `CLAUDE.md`
based on actual observed behavior rather than predicted behavior. This
document is the handoff artifact: everything decided here should be
sufficient context to resume work in Claude Code without re-deriving the
reasoning above.
