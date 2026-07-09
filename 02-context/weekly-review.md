---
type: reusable-pattern
last-updated: 2026-07-09
---

# Weekly Review Ritual

Memory systems don't fail dramatically — they rot quietly. This is the
maintenance pass that prevents it. Once a week, start a session and ask
Claude to "run the weekly review". Claude: work through this checklist
top to bottom, proposing changes rather than making them silently.

## Checklist

1. **Triage `00-inbox/`.** For each item, apply the classifier in
   `CLAUDE.md` and propose a destination: project note, entity, research
   note, decision, or (for preferences) an edit to
   `02-context/communication-style.md`. Empty inbox is the goal.
2. **Flag stale notes.** Any entity or context note with `last-updated`
   more than 60 days old: ask whether it's still accurate, update the
   date if confirmed, fix it if not.
3. **Reconcile `_index.md` with reality.** Every active project note
   should be listed; nothing listed should be missing or archived.
4. **Propose archives.** Any project with no session log in 30+ days:
   propose moving it to `99-archive/` per the ritual in
   `99-archive/README.md`.
5. **Check open threads.** Read the "Open Threads" section of each
   active project. Anything open across 3+ session logs gets called out
   as a decision waiting to be made.

## Output

End the review by writing a session log
(`03-sessions/YYYY-MM-DD-weekly-review.md`) listing what was triaged,
flagged, archived, and what needs the user's attention this week.
