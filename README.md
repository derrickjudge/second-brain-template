# 2nd Brain Template — Obsidian + MCP

A starter vault structure for giving Claude persistent memory across
sessions, using Obsidian as the storage layer and the Obsidian MCP server
as the connection to Claude.

See `demo/before-after.md` for a concrete example of the problem this solves.

## What's in here

```
CLAUDE.md              ← the ritual instructions Claude reads every session
_index.md              ← map of content, read second every session
00-inbox/               ← unsorted capture, triage manually
01-projects/            ← active project state (on-demand)
02-context/
  communication-style.md  ← ALWAYS-LOAD standing instruction
  (other)                  ← decisions, reusable patterns (on-demand)
03-sessions/            ← dated session logs (on-demand)
04-entities/            ← people, teams, customers — structured frontmatter
05-research/            ← topic-organized research notes
demo/before-after.md    ← the flagship demo transcript
```

## Setup

1. **Install Obsidian** (free): https://obsidian.md
2. **Open this folder as a vault** in Obsidian (Open folder as vault →
   select this repo).
3. **Install the Obsidian MCP server** and connect it to Claude Desktop or
   Claude.ai, following Obsidian's current MCP documentation. (This step
   changes as tooling evolves — check Obsidian's docs for the current
   setup flow rather than relying on a fixed guide here.)
4. **Edit `02-context/communication-style.md`** to reflect how you actually
   want Claude to write to you — this is the one file worth customizing
   before you do anything else.
5. **Start a session** and ask Claude to read `CLAUDE.md` and `_index.md`
   if it doesn't do so automatically, to confirm the connection works.

## The core idea

Every session, Claude follows a ritual: read the always-load context
(communication style) and the relevant on-demand context (active project,
recent session log, relevant entities) *before* responding — then, at the
end of the session, write back what happened and why. That write-back is
what most people skip, and it's the part that actually makes this a
*memory* system instead of just a pile of notes.

## Extending this

New content doesn't always obviously fit "projects" or "entities." Use the
classifier in `CLAUDE.md`:

> Does this need to shape behavior even when it's not the explicit topic
> of the conversation? If yes, it's always-load. If no, it's on-demand.

This is opinionated on purpose — one clear pattern is easier to fork and
adapt than a menu of options. Technical users comfortable with vector
search/RAG can layer that on top of this structure once the base pattern
is working; it's not needed to get real value out of this.
