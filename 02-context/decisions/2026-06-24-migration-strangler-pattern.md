---
type: decision
project: platform-migration-q3
date: 2026-06-24
status: active
---

# Decision — Q3 Migration Uses the Strangler Pattern, Not Big-Bang

## Decision
Migrate services off the legacy build system incrementally (strangler
pattern: new system runs alongside, services move one at a time behind a
routing layer) rather than a big-bang cutover weekend.

## Why
- Platform Engineering's systems are shared infrastructure — a failed
  big-bang cutover takes every product team down at once (see the
  standing note in
  [[04-entities/teams/platform-engineering|Platform Engineering]]).
- Incremental migration lets the two riskiest services (auth, billing)
  move last, after the pattern is proven on low-stakes services.
- Rollback per-service is a config change; rollback of a big-bang
  cutover is a second cutover weekend.

## Alternatives considered (and why rejected)
- **Big-bang cutover over a holiday weekend** — fastest calendar time,
  but concentrates all risk into one irreversible window; rejected on
  blast-radius grounds.
- **Indefinite parallel-run of both systems** — safest, but doubles
  maintenance load with no forcing function to finish;
  [[04-entities/people/jane-doe|Jane Doe]] rejected carrying two
  systems past Q3.

## Revisit when
More than two services need simultaneous migration to hit the Q3
deadline — at that point the incremental schedule no longer fits and
this needs re-deciding, not quiet schedule slip.
