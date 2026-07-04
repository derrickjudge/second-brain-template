---
type: session-log
project: second-brain-framework
date: 2026-07-02
---

# Session Log — 2026-07-02

## What was done
Worked through the full architecture with Claude: folder structure, the
always-load/on-demand classifier, and where communication style should
live (vault file, not just platform settings, so it's portable).

## Decisions made and why
- **Communication style lives in the vault, not just Claude.ai settings.**
  Why: platform settings don't travel to teammates or other agents. Vault
  file is portable and auditable. Native settings kept as a fallback/bridge
  only — a pointer, not a duplicate.
- **Flagship demo = session continuity.** Why: most relatable pain point,
  and solving it well requires the other use cases (decision log, reusable
  context) to exist too, so it's a superset, not a separate feature.
- **Opinionated single pattern (Obsidian + MCP) instead of a toolkit of
  options.** Why: easier to teach and fork; technical users can extend to
  RAG/vector search on their own once they understand the base pattern.

## Open threads
- Need to write the before/after transcript that makes the "cold start"
  pain concrete.
- Shared/team vault question (multiple contributors writing session logs)
  not yet resolved.

## Next steps
- Scaffold example entity notes (person, team, customer) and one research
  note to seed the repo.
- Draft the before/after demo.
