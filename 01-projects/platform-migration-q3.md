---
type: project
status: active
started: 2026-06-24
---

# Platform Migration Q3

## Goal
Move all services off the legacy build/deploy system onto the new
platform by end of Q3, owned by
[[04-entities/teams/platform-engineering|Platform Engineering]],
migration lead [[04-entities/people/priya-patel|Priya Patel]].

## Current State
Strangler-pattern migration underway. Routing layer is live; 3 of 11
services migrated (all low-stakes internal tools). Auth and billing are
deliberately scheduled last. On track for Q3, with no schedule buffer
left after the routing-layer work ran a week long.

## Key Decisions
- Strangler pattern over big-bang cutover — full reasoning in
  [[02-context/decisions/2026-06-24-migration-strangler-pattern|the decision note]].
- Auth-token handling in the routing layer was reworked after security
  review flagged tokens transiting the legacy path unencrypted (see
  2026-07-01 session log).

## Open Threads
- No schedule buffer remains; one more slip forces re-planning the
  service order (the "revisit when" condition in the decision note).
- Billing service owner hasn't confirmed their migration window yet.

## Next Steps
- Migrate services 4–6 (internal reporting cluster) by 2026-07-18.
- Get billing's migration window confirmed at the next infra sync.
- Dry-run the auth service migration in staging before end of July.
