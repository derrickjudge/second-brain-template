---
type: research
topic: ai-agent-memory
date-captured: 2026-07-02
status: summarized
---

# Context Window vs Persistent Memory

## Source
Internal notes + general industry discussion on agent memory architectures
(no single article — synthesized from multiple reads).

## Summary (in my own words)
A model's context window is short-term working memory — it resets between
sessions. A "2nd brain" vault is long-term memory living outside the model,
that gets selectively loaded back into the context window when relevant.
The design problem isn't "how do we store everything" — it's "what gets
loaded automatically vs. on request," because loading everything defeats
the purpose (cost, noise) and loading nothing defeats the purpose too
(no continuity). This is the same always-load/on-demand split used
elsewhere in this vault.

## Why this matters for the project
This is the theoretical grounding for the whole framework — worth
including in the workshop module as the "why does this work" section
before getting into the mechanics.

## Related
- [[01-projects/second-brain-framework|Second Brain Framework]]
- [[CLAUDE|CLAUDE.md classifier]]
