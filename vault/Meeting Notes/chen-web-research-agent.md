# Chen — Web Research Agent

## Overview

Chen (חן) is the web-research sub-agent of the 5-agents system. She is the top-of-funnel for the content pipeline: the CEO dispatches her with a topic, she searches the web, evaluates source quality against defined criteria, and deposits raw findings in `Content/` as markdown files for Yael to rewrite. Chen never produces finished content — she feeds the pipeline.

Chen is restricted via `tools:` frontmatter to `WebSearch, WebFetch, Read, Write, Edit, Glob, Grep` — no Bash, no external API, no agent dispatch. Her defining feature is a persistent memory system in `chen/Memory/searches.md`: before every search she checks for similar queries within the last 30 days; if a match is found she surfaces it and asks the user whether to reuse or redo. After every search she appends a structured log entry. This prevents redundant searches and builds a searchable research archive.

Pipeline position: CEO → **Chen** (finds raw material) → Yael (rewrites in house style) → CEO (illustrates via Yuval) → Output/.

## Open Questions

- `searches.md` grows unbounded — should there be a pruning policy (e.g., archive entries older than 90 days)?
- Should Chen deposit multiple source files per search (top 2) or always exactly 1 file per request?
- Should the CEO surface Chen's output to the user for review before automatically passing it to Yael, or route directly?

## Session Log

### 2026-05-06 — Initial implementation [shipped]
- **What was done:** Created `.claude/agents/chen.md` with `tools: WebSearch, WebFetch, Read, Write, Edit, Glob, Grep` frontmatter (the load-bearing restriction). Created `chen/Memory/searches.md` (header-only; Chen appends entries at runtime). Created `chen/agent.md` (human pointer). Updated `ceo.md`: added Chen to Agent Roster, added Web Research Routing section with Hebrew + English trigger keywords. Updated `CLAUDE.md` hierarchy table (Chen row, Active). Created `vault/Code Reference/chen-agent.md` and updated both vault indexes.
- **Decisions:** Tool set chosen to allow web access (WebSearch, WebFetch) while preventing shell access, API side-effects, and agent dispatch — same pattern as Yael but with web tools added. 30-day memory window balances freshness vs. avoiding redundant searches. Chen deposits raw fetched text (no rewriting) to keep her scope narrow; rewriting is Yael's job, preserving separation of concerns. Slug-based filenames in `Content/` (YYYY-MM-DD-topic-slug) chosen over user-facing titles to avoid filesystem special-character issues.
- **Notes / Caveats:** `chen/Memory/searches.md` starts empty; it grows as Chen runs real searches. The pruning policy for the memory log is an open question — left for a future session. Chen self-heals a missing `searches.md` (creates it), so the initial file is documentation scaffolding rather than a hard dependency.
- **Related:** [[ceo-agent]], [[yael-agent]], [[yuval-agent]], [[chen-agent]]
