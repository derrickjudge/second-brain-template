---
type: reusable-pattern
last-updated: 2026-07-09
---

# Team Vault Conventions

How this pattern holds up when multiple people write to the same vault.
Solo users can ignore this file entirely — nothing else depends on it.

## Attribution

- Every session log gets an `author:` field in frontmatter (initials or
  short name) and the filename gains an author suffix:
  `2026-07-09-second-brain-framework--dj.md`.
  Two people can then log sessions against the same project on the same
  day without colliding.
- Entity and project notes stay unowned — they're shared state. The git
  history is the attribution for those.

## Merging

Git is the merge layer; no sync tooling is needed at team scale:

- Session logs are append-only, dated, and per-author, so conflicts are
  structurally rare — two people never edit the same log file.
- The genuinely shared files (`_index.md`, project notes) are the only
  realistic conflict surface. Convention: whoever ends their session
  last pulls before pushing, and project-note edits go at the *end* of a
  session, not throughout, to keep the window small.
- If a real conflict happens, both versions are markdown — resolve like
  any prose conflict, and note the resolution in your session log.

## Standing instructions in a shared vault

The always-load slot stays singular: `02-context/communication-style.md`
belongs to the vault owner (or, for a true team vault, describes the
*team's* shared voice). Individual styles live one-per-person in
`02-context/people-styles/<name>.md`, and the session-start ritual loads
the file matching the current session's author. Don't merge multiple
people's preferences into one file — that's how contradictory
instructions accumulate.

## What deliberately doesn't change

The ritual itself is identical solo or shared. That's the point: a
teammate joining the vault inherits working memory on day one by reading
the same files Claude does.
