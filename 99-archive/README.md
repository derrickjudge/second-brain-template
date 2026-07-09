# Archive

Completed and parked projects live here so `01-projects/` and `_index.md`
only ever show what's actually active.

## The archival ritual

When a project's `status:` becomes `done` or `parked`:

1. Create `99-archive/<project-slug>/`.
2. Move the project note and all of its session logs into it.
3. Replace its `_index.md` entry with a one-line tombstone under an
   "Archived" heading — name, dates, one-clause outcome.
4. Leave decision notes in `02-context/decisions/` where they are —
   decisions outlive the projects that produced them and stay queryable.

Claude should *propose* archiving at session end when a project has been
inactive for 30+ days or is explicitly closed — never archive silently
(see `CLAUDE.md`).

Nothing is deleted; archives stay greppable and linkable. Restoring a
project is the same ritual in reverse.
