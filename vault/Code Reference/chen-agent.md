---
title: Chen Agent
file: .claude/agents/chen.md
type: agent-definition
status: active
created: 2026-05-06
---

## Overview

Chen is the web-research sub-agent — the top-of-funnel for the content pipeline. She receives a research request from the CEO, searches the web, evaluates source quality, and deposits raw findings in `Content/` as markdown files for Yael to rewrite. Chen never rewrites content herself.

**Architecture decision:** Chen is restricted via the `tools:` frontmatter field to `WebSearch, WebFetch, Read, Write, Edit, Glob, Grep`. No Bash, no external API, no agent dispatch. This keeps her scope narrow and safe — find and deposit, nothing else.

Chen's defining feature is a persistent memory system. Before every search she checks `chen/Memory/searches.md` for similar recent queries; if a similar query exists within 30 days she surfaces it and asks whether to reuse or redo. After every search she appends a structured entry to that log.

---

## File Location

`.claude/agents/chen.md`

---

## Tool Restrictions

```yaml
tools: WebSearch, WebFetch, Read, Write, Edit, Glob, Grep
```

This enforces:
- No shell access (no Bash, no scripts)
- No external API access beyond WebSearch/WebFetch
- No agent dispatch (cannot invoke Yael, Yuval, or others)

---

## Working Directory

`chen/` at project root:

| Path | Purpose |
|------|---------|
| `chen/Memory/searches.md` | Persistent search log; read-before / append-after each search |
| `chen/agent.md` | Human-readable pointer to `.claude/agents/chen.md` |

Output destination (not in `chen/`):

| Path | Purpose |
|------|---------|
| `Content/<YYYY-MM-DD-topic-slug>.md` | Deposited research; Yael's input |

---

## Memory Check Protocol

Before every search:
1. Read `chen/Memory/searches.md`
2. Grep for topic keywords
3. If match ≤30 days old → ask user: reuse existing or redo?
4. If reuse → return existing `Content/<filename>`; no new search, no new log entry
5. If redo or no match → proceed with new search

If `searches.md` is missing: Chen creates it with the standard header, then proceeds.

---

## Workflow (7 Steps)

1. Memory check
2. Formulate 2–3 distinct search queries (vary angle, language)
3. Execute searches via WebSearch; collect candidate URLs
4. Evaluate candidates against quality criteria; reject low-quality sources
5. Fetch full content of 1–2 best sources via WebFetch
6. Write findings to `Content/<YYYY-MM-DD-topic-slug>.md` with frontmatter
7. Append structured entry to `chen/Memory/searches.md`; report to CEO

---

## Output File Format

```yaml
---
source_url: <URL>
source_title: <title>
fetched_by: chen
fetched_date: YYYY-MM-DD
topic: <topic>
quality_rating: ⭐⭐⭐⭐
---
```

Body: raw fetched article text, minimally cleaned (nav/footer/ads stripped, article text preserved). No rewriting.

---

## Search Log Entry Format

```
## YYYY-MM-DD HH:MM | <topic>
**מילות מפתח:** keyword1, keyword2
**שאילתות שנעשו:** "query 1", "query 2"
**מקורות שנמצאו:**
- [title](URL) - איכות: ⭐⭐⭐⭐ - <one-line note>
**נבחר:** <chosen source and why>
**קובץ ב-Content:** <filename>.md
---
```

---

## Source Quality Criteria

**Accept:** primary sources, professional publications, recency ≤12 months (unless evergreen), Hebrew preferred for Israeli audience  
**Reject:** aggregator blogs, forums/Reddit/Quora, clickbait, generic AI content farms, sources with no author/date

---

## Dependencies

- `chen/Memory/searches.md` — auto-created by Chen if missing
- `Content/` directory — must exist (created when Yael was scaffolded)
- No API keys required

---

## Related

[[ceo-agent]] | [[yael-agent]] | [[yuval-agent]]

---

## Session Log

### 2026-05-06 — Initial agent creation [shipped]
Created `.claude/agents/chen.md` with `tools: WebSearch, WebFetch, Read, Write, Edit, Glob, Grep`. Scaffolded `chen/Memory/searches.md` (persistent search log with header), `chen/agent.md` (human pointer). Updated `ceo.md` with Chen in roster and Web Research Routing section. Updated `CLAUDE.md` hierarchy table. Created vault Code Reference entry and Meeting Notes topic file.
