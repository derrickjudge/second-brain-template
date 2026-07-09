# Before / After: Session Continuity

Same person, same project, three weeks apart, starting a new chat both times.

---

## Before (no vault)

**User:** Hey, can you help me finish the pricing proposal for Acme?

**Claude:** I'd be happy to help! Could you give me some context — what's
the pricing model you're working with, who's the audience, and what's been
discussed with Acme so far?

**User:** Ugh, ok — so Acme is mid-market, Sam Rivera is our contact, they're
on Platform + Premium support, they've asked twice about bulk-import which
we don't support yet, we already had a renewal call in June where I said I'd
follow up with product on that gap, and last time we talked about pricing I
was leaning toward a 10% discount tied to a 2-year commit but hadn't decided...

*(Five minutes of re-explaining before the actual work starts.)*

---

## After (vault connected)

**User:** Hey, can you help me finish the pricing proposal for Acme?

**Claude:** *[reads `CLAUDE.md`, `_index.md`,
`01-projects/acme-widgets-pricing-proposal.md`, and the latest session
log in `03-sessions/`]*

Picking this up — the proposal's drafted: Platform + Premium support,
10% discount tied to a 2-year commit (the reasoning's in the June 27
decision note — the 2-year term buys runway on the bulk-import gap Sam
keeps raising). Per the July 5 session log, you're blocked on legal's
review of the commit clause, and your own next step was to chase them
if nothing came back by July 10.

So: has legal responded? If yes, the remaining steps are sending it to
Sam and booking the walkthrough call — he prefers a short call over a
long document. If not, today's job is the chase.

---

## What changed

Nothing about Claude's underlying capability changed — the difference is
entirely that relevant context was already loaded before the user had to
ask for help. The second version knows the deal structure, *why* it was
chosen, what's blocking, and even the contact's communication
preference — none of which the user had to repeat.

Just as important: when the vault *doesn't* have an answer, Claude says
"not captured" and offers to start a note, instead of inventing
something plausible (see the gap beat in `demo-script.md`, Demo 1).
Memory you can't trust to admit gaps isn't memory.

This is the whole value proposition of the pattern: not "Claude gets
smarter," but "Claude stops starting from zero."
