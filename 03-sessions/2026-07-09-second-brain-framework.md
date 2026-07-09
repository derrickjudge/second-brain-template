---
type: session-log
project: second-brain-framework
date: 2026-07-09
---

# Session Log — 2026-07-09

## What was done
Built out the vault from single-example scaffolding to demo-ready:

- **New patterns:** `_templates/` (7 skeletons), decision log
  (`02-context/decisions/`), archive lifecycle (`99-archive/` + ritual),
  team-vault conventions, weekly-review ritual.
- **Demo data:** extended the fictional Acme world — 2 new projects
  (a customer pricing proposal, an infra migration) with 5 session logs
  spanning 2026-06-20 → 07-05, 6 new entities (three people, one team,
  two customer accounts), 2 decision notes, 1 research note (tiered
  memory), 3 inbox captures designed for live triage. (Entity names
  deliberately not repeated here — a cold-start test showed this meta
  log polluting entity searches for the fictional world.)
- **Demo tooling (content only):** `demo/demo-script.md` with four
  runnable demos; amended `demo/before-after.md` to match the new vault
  state; updated `CLAUDE.md`, `_index.md`, `README.md`.

## Decisions made and why
- **Demo data stays fictional (Acme world), shipped in the template.**
  Why: safe to show any audience and the demos work for anyone who
  forks the repo; real-work data can be layered on privately.
- **No executable tooling yet (linter, wrap-up skill).** Why: crosses
  into the tests-required rigor tier per `CLAUDE.md`; content-only
  changes keep this iteration fast and the repo shippable.
- **Second standing-instruction example added inside the churn-risk
  customer's note.** Why: one example (the infra team's) looks like a
  gimmick; two establishes it as a pattern, and the customer-flavored
  one demos well for non-engineering audiences.
- **Before/after transcript amended rather than dated.** Why: the
  vault now contains a pricing project note, so the old "no project
  note exists" beat became false; the transcript must always match
  shipped vault state or the flagship demo undermines itself.

## Open threads
- Ritual still not live-tested against a real Obsidian + MCP
  connection (carried over from `DESIGN.md` §6).
- Deferred tooling list lives in the project note.

## Next steps
- Rehearse all four demos against a live connection; iterate
  `CLAUDE.md` wording on any misfire.
- Then: workshop module extraction.
