---
type: research
topic: ai-agent-memory
date-captured: 2026-07-09
status: summarized
---

# Tiered Memory Patterns (Hot / Warm / Cold)

## Source
Survey of 2026 writing on agent memory architectures, including a
DEV Community piece on markdown-file memory management
(dev.to/imaginex), a walkthrough of a 4-level agent memory system
(Andy G., Medium), and several public Obsidian-as-agent-memory repos
(jrcruciani/obsidian-memory-for-ai, AgriciDaniel/claude-obsidian).

## Summary (in my own words)
The pattern that keeps recurring: memory works best in tiers, sorted by
how often it's touched, not by topic.

- **Hot** — the current context window. Expensive, tiny, resets every
  session. Nothing "lives" here; things are *loaded* here.
- **Warm** — recent activity: session logs, active project notes.
  Appended constantly, read at session start, ages out naturally.
- **Cold** — curated long-term knowledge: distilled decisions, entity
  facts, standing instructions. Written rarely, deliberately, after the
  fact has proven durable.

This vault maps onto the tiers cleanly: `03-sessions/` and active
`01-projects/` notes are warm; `02-context/`, `04-entities/`, and
`05-research/` are cold; the always-load/on-demand classifier decides
what gets promoted into hot at session start. The failure mode the
tiers guard against is also the one named in
[[05-research/ai-agent-memory/context-window-vs-persistent-memory|the
earlier note]]: loading everything (cost, noise) or nothing (no
continuity). A second confirmation from the survey: session logs with a
date-plus-slug naming convention and append-only discipline are the de
facto standard across implementations — matches what this vault already
does.

## Why this matters for the project
Gives the workshop a vocabulary attendees may already have seen
("hot/warm/cold") and positions the vault as an instance of a
recognized pattern rather than an invention — useful credibility for
the "why does this work" section.

## Related
- [[01-projects/second-brain-framework|Second Brain Framework]]
- [[05-research/ai-agent-memory/context-window-vs-persistent-memory|Context Window vs Persistent Memory]]
