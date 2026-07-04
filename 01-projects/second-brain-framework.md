---
type: project
status: active
started: 2026-07-02
---

# Second Brain Framework

## Goal
Build a template repo + workshop module teaching individuals and teams how
to give Claude persistent memory using an Obsidian vault + MCP server,
so they get better multi-session results without re-explaining context
every time.

## Current State
Architecture locked. Folder structure defined: projects, context, sessions,
entities, research, inbox. Core mechanic is the session-start/session-end
ritual enforced via `CLAUDE.md`. Classifier defined for always-load vs
on-demand content.

## Key Decisions (see session logs for full "why")
- Flagship demo = session continuity (not decision-log or cross-project
  reuse) — most visceral before/after.
- Obsidian + MCP over pure vector/RAG — transparency and no-code usability
  for non-technical users beats semantic search at this scale.
- One opinionated pattern, not a menu of options — easier to teach, easier
  to fork.

## Open Threads
- Wording of the before/after demo transcript
- How the pattern handles a shared team vault (multiple people writing
  session logs)

## Next Steps
- Finish scaffolding example entity + research notes
- Write before/after demo transcript
- Turn into workshop module once repo is solid
