# Vault Instructions for Claude

    Rigor: demo         # polished, shareable GitHub template; tests for core logic
    Hosting: local      # vault + Obsidian + MCP all run on the user's machine

This vault is a "2nd brain" — persistent memory and context that lives outside
any single conversation. Follow the rituals below every time you interact with it.

Note on the declarations above: this file is a *vault ritual* doc, not a
code-style guide, but the project as a whole (this template repo) is meant to
be shared publicly for others to fork — hence `demo` rather than `poc`. If
tooling code is added later (e.g. a shared-vault sync script), it should get
tests for its core logic and pass typing/linting before being called done, but
doesn't need the full TDD/coverage bar of a `production` project.

## On EVERY session start, in this order:

1. **Read `02-context/communication-style.md` first, always.**
   This is a standing instruction, not reference material — it shapes how you
   write and respond for the rest of the session, regardless of topic.

2. **Read `_index.md`** for a map of active projects and key context notes.

3. **If the conversation is about a specific project**, read that project's
   note in `01-projects/` and its most recent entry in `03-sessions/`
   (session logs are named `YYYY-MM-DD-[project-slug].md`, so the latest
   for a project is findable by filename) before doing anything else. Do
   not ask the user to re-explain context that already exists in these
   files. If the project note and the latest session log disagree, the
   session log is ground truth — the project note is the digest, and
   flagging the drift is part of the job.

4. **Look up entities on demand.** If a person, team, or customer is
   mentioned, check `04-entities/` before asking the user who they are.

5. **Check the decision log for any question about past decisions** —
   "why did we...", "what did we decide about...", or a proposal to
   revisit a choice. Check `02-context/decisions/` before reasoning from
   scratch — the note has the reasoning *and the alternatives already
   rejected*. If no decision note exists, say so plainly rather than
   reconstructing a plausible answer.

## During the session:

- If you learn something durable (a decision, a reusable pattern, a fact
  about a person/team/customer), say so and offer to write it to the
  appropriate file. Don't write silently — the user should know what's
  being saved and where.
- When creating a new note, copy its skeleton from `_templates/` so
  frontmatter stays consistent and queryable.
- A decision worth citing later gets its own note in
  `02-context/decisions/` (template: `_templates/decision.md`), named
  `YYYY-MM-DD-short-slug.md` — decision, why, alternatives rejected,
  revisit-when.
- Use the classifier below when unsure where new information belongs.

## On session end (when the user indicates they're wrapping up, or asks you to):

Append a new entry to `03-sessions/YYYY-MM-DD-[project-slug].md` with:
- What was done
- Decisions made **and why** (the "why" is the part that gets lost otherwise)
- Open threads / unresolved questions
- Suggested next steps

If the project note in `01-projects/` is now stale (state has materially
changed), update it too — don't just log the session and leave the project
note behind.

Also at session end: if any project has had no session log for 30+ days,
or was explicitly closed this session, *propose* archiving it per the
ritual in `99-archive/README.md`. Never archive silently.

(For the weekly maintenance pass — inbox triage, stale notes, index
reconciliation — see `02-context/weekly-review.md`; run it when the user
asks for the weekly review.)

---

## The Always-Load vs On-Demand Classifier

When adding a new kind of content to this vault, ask:

> **Does this need to shape behavior even when it's not the explicit topic
> of the conversation?**

- **Yes → Always-load.** It's a lens (like communication style). Add a
  pointer to it in step 1 above.
- **No → On-demand.** It's a fact (like a project's state or a customer's
  contact info). It lives in its folder and gets read only when relevant.

Watch for standing instructions hiding inside on-demand data — e.g. an
entity note that says "always flag security implications for this team."
That single line may need to be promoted to always-load even though the
rest of the note is on-demand reference data.

## Folder Map

| Folder | Type | Loading |
|---|---|---|
| `02-context/communication-style.md` | Standing instruction | Always-load |
| `02-context/decisions/` | One note per durable decision (what, why, rejected alternatives) | On-demand (check for "why" questions) |
| `02-context/` (other) | Reusable patterns, rituals, conventions | On-demand |
| `01-projects/` | Active project state | On-demand |
| `03-sessions/` | Dated session logs | On-demand (latest read when project is active) |
| `04-entities/` | People, teams, customers (structured frontmatter) | On-demand |
| `05-research/` | Topic notes: source + your-words summary + links | On-demand |
| `00-inbox/` | Unsorted capture, triaged manually (or via weekly review) | N/A |
| `_templates/` | Skeletons for each note type — copy when creating notes | N/A |
| `99-archive/` | Done/parked projects + their session logs | Not loaded (greppable) |
