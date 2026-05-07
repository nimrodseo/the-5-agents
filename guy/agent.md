# Guy — QA Agent

Canonical agent definition: `.claude/agents/guy.md`

## Working Directory

| Path | Purpose |
|------|---------|
| `guy/QA_Reports/` | Historical log of every QA report — one `.md` per review session |

## Reads From

| Path | Purpose |
|------|---------|
| `Output/<filename>.md` | The finished artifact under review |
| `yael/style-guide.md` | Style compliance check |
| `chen/Memory/searches.md` | Source attribution check (when output came from Chen) |

## Writes To

`guy/QA_Reports/<YYYY-MM-DD-HHMM>-<slug>.md` — only. Guy does not edit output files.

## To Invoke

Ask the CEO to QA a finished output. Trigger keywords:

**Hebrew:** בדוק, אמת, QA, ביקורת, איכות, אישור  
**English:** check, verify, QA, review, validate, approve, audit

Guy also runs **automatically** at the end of every content pipeline — no explicit trigger needed.

## Tool Restrictions

`tools: Read, Glob, Grep, Write`

No Bash. No WebSearch. No Edit on existing files. No agent dispatch.

## Role in the Pipeline

```
CEO → Chen → CEO → Yael → CEO → Yuval → CEO → Yael (final) → CEO → Guy → CEO → User
```

Guy is the last checkpoint. Nothing reaches the user without his ✅.
Maximum 3 review rounds per output. If round 3 fails, CEO escalates to user.
