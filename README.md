# 2nd Brain Template — Obsidian + MCP

A starter vault structure for giving Claude persistent memory across
sessions, using Obsidian as the storage layer and the Obsidian MCP server
as the connection to Claude.

See `demo/before-after.md` for a concrete example of the problem this
solves, and `demo/demo-script.md` for four runnable demos. The vault
ships pre-populated with a fictional company (Acme Corp and its
customers) so the demos work out of the box — replace that world with
your own as you go.

## What's in here

```
CLAUDE.md              ← the ritual instructions Claude reads every session
_index.md              ← map of content, read second every session
_templates/             ← skeleton note for each content type
00-inbox/               ← unsorted capture, triaged manually or via weekly review
01-projects/            ← active project state (on-demand)
02-context/
  communication-style.md  ← ALWAYS-LOAD standing instruction
  decisions/               ← one note per durable decision, with the "why"
  team-vault-conventions.md ← how the pattern works with multiple writers
  weekly-review.md         ← the maintenance ritual that prevents rot
03-sessions/            ← dated session logs (on-demand)
04-entities/            ← people, teams, customers — structured frontmatter
05-research/            ← topic-organized research notes
99-archive/             ← done/parked projects, per the ritual in its README
demo/
  before-after.md       ← the flagship before/after transcript
  demo-script.md        ← four runnable demos with exact prompts
```

## Use cases

The one pattern covers several distinct jobs — each is demoable (see
`demo/demo-script.md`):

1. **Session continuity** (flagship) — a new session picks up
   mid-project without re-explaining anything.
2. **Entity lookup + standing instructions** — facts about people,
   teams, and customers load on demand, and instructions embedded in
   them ("always flag security implications", "check open tickets
   before upselling") fire without being asked.
3. **Decision recall** — "why did we choose X?" answered from the
   decision log, including the alternatives that were rejected.
4. **Inbox triage** — quick captures get classified into the right
   folder using the always-load/on-demand rule.
5. **Session write-back** — Claude logs what happened and *why* at
   session end; this is what makes it memory instead of notes.
6. **Weekly review** — a maintenance ritual (stale notes, index drift,
   archive proposals) that keeps the vault trustworthy over months.

## Setup

1. **Install Obsidian** (free): https://obsidian.md
2. **Open this folder as a vault** in Obsidian (Open folder as vault →
   select this repo).
3. **Connect Claude — two paths:**
   - *Claude Desktop / Claude.ai:* install the Obsidian MCP server and
     connect it, following Obsidian's current MCP documentation. (This
     step changes as tooling evolves — check Obsidian's docs for the
     current setup flow rather than relying on a fixed guide here.)
   - *Claude Code:* no MCP server needed — open a terminal in the vault
     folder and start Claude Code; `CLAUDE.md` is picked up natively.
     Obsidian remains your GUI for browsing and editing the same files.
4. **Edit `02-context/communication-style.md`** to reflect how you actually
   want Claude to write to you — this is the one file worth customizing
   before you do anything else.
5. **Start a session** and ask Claude to read `CLAUDE.md` and `_index.md`
   if it doesn't do so automatically, to confirm the connection works.

## The core idea

Every session, Claude follows a ritual: read the always-load context
(communication style) and the relevant on-demand context (active project,
recent session log, relevant entities) *before* responding — then, at the
end of the session, write back what happened and why. That write-back is
what most people skip, and it's the part that actually makes this a
*memory* system instead of just a pile of notes.

## Extending this

New content doesn't always obviously fit "projects" or "entities." Use the
classifier in `CLAUDE.md`:

> Does this need to shape behavior even when it's not the explicit topic
> of the conversation? If yes, it's always-load. If no, it's on-demand.

This is opinionated on purpose — one clear pattern is easier to fork and
adapt than a menu of options. Technical users comfortable with vector
search/RAG can layer that on top of this structure once the base pattern
is working; it's not needed to get real value out of this.
