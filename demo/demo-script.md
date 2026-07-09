# Demo Script — Four Runnable Demos

Each demo below is runnable against this vault as shipped: every
scripted question has a note that answers it, and one question
deliberately doesn't (that gap is the point — see Demo 1).

**Connection setup (either works; behavior is the same):**

- **Claude Desktop / Claude.ai + Obsidian MCP server** — the README
  setup path. Claude reads the vault through MCP tools; you may need to
  say "read CLAUDE.md first" in the very first message of a session if
  it doesn't do so on its own.
- **Claude Code opened in the vault folder** — `cd` into the vault and
  start Claude Code. No MCP server needed; `CLAUDE.md` is picked up
  natively, which usually makes the ritual fire without prompting.
  Best for technical audiences.

Reset between rehearsals with git: `git checkout .` discards any
session logs or note edits a practice run wrote.

---

## Demo 1 — Cold-start continuity (the flagship) · ~5 min

**The claim:** a brand-new session picks up mid-project without the
user re-explaining anything.

**Setup:** fresh session, nothing said yet.

**Type:**
> Pick up the Acme pricing proposal where we left off — what's the
> state and what should I do today?

**What should happen:** Claude reads `CLAUDE.md`, `_index.md`, then
`01-projects/acme-widgets-pricing-proposal.md` and the latest session
log (`03-sessions/2026-07-05-...`), and answers with: proposal drafted,
10%/2-year structure, **blocked on legal review of the commit clause
sent 07-05**, and — since today is past 07-10 if you're demoing later —
that it's time to chase legal. No re-explaining happened.

**Point at on screen:** the session log's "Open threads" section next
to Claude's answer — the answer is visibly *from the vault*, not
improvised.

**The gap beat (do this second, same session) — type:**
> Also, what did we decide about NorthStar's renewal pricing?

**What should happen:** Claude checks
`04-entities/customers/northstar-logistics.md`, finds renewal is
2027-02 with *nothing decided*, and says so — then offers to start a
note when the discussion begins. **This is the trust moment:** the
system says "not captured" instead of inventing an answer. Memory
you can't trust to admit gaps isn't memory.

---

## Demo 2 — Standing instruction fires unprompted · ~3 min

**The claim:** instructions embedded in entity data change Claude's
behavior even when nobody mentions them.

**Setup:** fresh session (or continue from Demo 1).

**Type:**
> Draft a quick status update on the Q3 platform migration for Marcus.

**What should happen:** Claude reads the project note, the team note,
and `marcus-chen.md` — and the draft (a) is a one-page summary, because
Marcus's note says "no summary, no meeting", and (b) mentions security
posture (the auth-token rework), because the Platform Engineering note
says *always flag security implications* for this team's projects.
Nobody asked for either.

**Point at:** the ⚠️ standing note in
`04-entities/teams/platform-engineering.md` — one line of on-demand
data acting like an always-load instruction. Bonus: repeat the trick
with "should we pitch BluePeak the Premium support tier?" — the
BluePeak note's standing instruction should make Claude check the open
tickets and advise against pitching until they clear.

---

## Demo 3 — Decision recall with the "why" · ~3 min

**The claim:** the vault remembers not just what was decided but why,
and what was rejected.

**Type:**
> Why did we go with a 2-year commit for Acme instead of just a bigger
> discount?

**What should happen:** Claude cites
`02-context/decisions/2026-06-27-acme-pricing-discount-structure.md`:
the 2-year term buys runway on the bulk-import gap and clears
procurement's re-evaluation cycle; the flat-15% and
contractual-bulk-import alternatives were considered and rejected, with
reasons. Follow up with "what would make us revisit that?" — the
decision note has an explicit answer.

**Point at:** the "Alternatives considered" section — this is the
content that a to-do list or status doc never captures and that vanishes
from human memory in about two weeks.

---

## Demo 4 — Inbox triage + session write-back · ~7 min

**The claim:** the vault isn't read-only context — Claude maintains it,
and the write-back is what makes it *memory* rather than notes.

**Type:**
> Let's triage the inbox.

**What should happen:** Claude works through the three captures in
`00-inbox/`, applying the classifier out loud:

1. **Dana Okafor** → new person entity in `04-entities/people/`,
   linked from the Product team note (which already flags her as
   pending). On-demand: it's a fact.
2. **Onboarding checklist idea** → genuinely ambiguous (project?
   feature request? research?). Claude should reason about it and
   propose, not just file it — the discussion is the demo.
3. **"Just recommend one" preference** → the classifier's yes-case:
   it must shape *every* session, so it's an edit to
   `02-context/communication-style.md`, not a filed note.

Approve the proposals and let Claude write the files — it should never
write silently (per `CLAUDE.md`).

**Then end the session — type:**
> That's it for today, wrap up.

**What should happen:** Claude appends a dated session log to
`03-sessions/` with what was done, decisions *and why*, open threads,
next steps. Open the file live.

**Closing line for the audience:** "Next week, a brand-new session
reads that file and starts exactly here. That write-back is the whole
trick — everything else is folder structure."

---

## If a demo misfires

The ritual is prompt-enforced, not guaranteed. If Claude skips a step
(doesn't read the session log, asks you to re-explain), the recovery
*is itself a demo*: say "check the vault first, per CLAUDE.md" and let
it correct. Note what it skipped — that's exactly the feedback loop for
iterating `CLAUDE.md` wording described in `DESIGN.md` §6.
