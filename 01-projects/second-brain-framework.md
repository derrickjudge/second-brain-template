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
Architecture locked and demo-ready. Folder structure defined: projects,
context, sessions, entities, research, inbox — plus templates, a decision
log, an archive lifecycle, and team-vault conventions (added 2026-07-09).
Vault is populated with a fictional Acme world rich enough to run the
four demos in `demo/demo-script.md`. Core mechanic is the
session-start/session-end ritual enforced via `CLAUDE.md`. Classifier
defined for always-load vs on-demand content.

## Key Decisions (see session logs for full "why")
- Flagship demo = session continuity (not decision-log or cross-project
  reuse) — most visceral before/after.
- Obsidian + MCP over pure vector/RAG — transparency and no-code usability
  for non-technical users beats semantic search at this scale.
- One opinionated pattern, not a menu of options — easier to teach, easier
  to fork.

## Open Threads
- The session ritual hasn't been live-tested against a real Obsidian +
  MCP connection yet — demo-script wording may need iteration after the
  first real run (see "If a demo misfires" in `demo/demo-script.md`).
- Deferred tooling: vault linter (broken wikilinks, stale notes, missing
  frontmatter) and Claude Code skills for wrap-up/triage — deliberately
  not built yet because they cross into the tests-required rigor tier.

## Next Steps
- Rehearse the four demos in `demo/demo-script.md` against a live
  connection; fix any ritual misfires by iterating `CLAUDE.md`.
- Turn into workshop module once the demos run clean.
- Decide whether the deferred tooling is worth building before or after
  the workshop.
