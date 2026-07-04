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

**Claude:** *[reads `CLAUDE.md`, `_index.md`, `04-entities/customers/acme-widgets-co.md`]*

Picking this up — Acme's mid-market, on Platform + Premium support, Sam
Rivera is your primary contact. Per the customer note, the bulk-import gap
came up again on the June 15 renewal call and you flagged it to product.

For the pricing proposal itself — I don't see a project note or session
log for it yet, so this looks like it's starting fresh. Want to base it on
the standard mid-market tier, or is there a discount/commitment structure
you were already leaning toward? If you mentioned one in an earlier
conversation that wasn't logged, that's worth capturing in a project note
now so it doesn't get lost again.

---

## What changed

Nothing about Claude's underlying capability changed — the difference is
entirely that relevant context was already loaded before the user had to
ask for help. The second version also does something the first can't:
it notices *what's missing* (no project note for the pricing proposal)
and offers to fix that gap going forward, instead of just answering once
and losing the thread again.

This is the whole value proposition of the pattern: not "Claude gets
smarter," but "Claude stops starting from zero."
