---
title: Guy Agent
file: .claude/agents/guy.md
type: agent-definition
status: active
created: 2026-05-07
---

## Overview

Guy is the QA gatekeeper — the 5th and final active sub-agent in the content pipeline. He receives finished outputs from the CEO, runs a structured 5-category checklist, writes a QA report to `guy/QA_Reports/`, and returns a pass/fail verdict. Nothing reaches the user without his ✅.

**Architecture decision:** Guy is restricted to `tools: Read, Glob, Grep, Write`. No Edit, no Bash, no Web, no agent dispatch. Write is used exclusively to create new QA report files — he cannot modify outputs, style guides, or any other file. This enforces the separation: Guy judges, Yael fixes, the CEO orchestrates between them.

Guy closes the loop via the CEO: on ❌, the CEO re-briefs Yael with Guy's correction notes and returns the revised output to Guy. After 3 failed rounds the CEO escalates to the user.

---

## File Location

`.claude/agents/guy.md`

---

## Tool Restrictions

```yaml
tools: Read, Glob, Grep, Write
```

This enforces:
- No shell access
- No web access
- No editing of any file (Write is for creating new reports only)
- No agent dispatch

---

## Working Directory

`guy/` at project root:

| Path | Purpose |
|------|---------|
| `guy/QA_Reports/` | Historical log of every QA report; one `.md` per review |
| `guy/agent.md` | Human-readable pointer to `.claude/agents/guy.md` |

Guy also reads (but never writes):

| Path | Purpose |
|------|---------|
| `Output/<filename>.md` | Artifact under review |
| `yael/style-guide.md` | Style compliance reference |
| `chen/Memory/searches.md` | Source attribution (when output originated from Chen) |

---

## Workflow (7 Steps)

1. Read the output (`Output/<filename>.md`)
2. Read `yael/style-guide.md` for style check
3. Grep `chen/Memory/searches.md` for source entry (if content came from Chen)
4. Run the 5-category QA checklist
5. Write report to `guy/QA_Reports/<YYYY-MM-DD-HHMM>-<slug>.md`
6. Return verdict to CEO: ✅ or ❌ + report path
7. If ❌: provide 2–3 line correction brief for the CEO to pass to Yael

---

## QA Checklist (5 Categories)

1. **רלוונטיות לבריף** — content answers the original brief, no deviations
2. **סגנון ומיתוג** — tone, style, language consistency per `yael/style-guide.md`
3. **שלמות מבנית** — headline, opening, summary/CTA, source attribution
4. **תמונות** — all `{{IMAGE_NEEDED}}` replaced, relevance, alt text/captions
5. **שלמות טכנית** — no typos, no broken markdown, no redundant repetition

---

## Report Naming Convention

`guy/QA_Reports/<YYYY-MM-DD-HHMM>-<slug>.md`

Slug = output filename, extension stripped, spaces → dashes.

---

## QA Loop Protocol (CEO-Side)

- Round 1–2: ✅ → present to user. ❌ → CEO re-briefs Yael → Guy reviews again.
- Round 3: ❌ → CEO presents output + QA report to user; requests manual decision.
- CEO logs every QA pass to vault (round, verdict, report path, flags if ❌).

---

## Dependencies

- `Output/` directory — must exist (created with Yael scaffold)
- `yael/style-guide.md` — soft dependency; Guy skips style check if missing, reports it
- No API keys required

---

## Related

[[ceo-agent]] | [[yael-agent]] | [[chen-agent]] | [[yuval-agent]]

---

## Session Log

### 2026-05-07 — Initial agent creation [shipped]
Created `.claude/agents/guy.md` with `tools: Read, Glob, Grep, Write` — no Edit enforces read-only on all outputs. Scaffolded `guy/QA_Reports/` (git-tracked via `.gitkeep`) and `guy/agent.md`. Updated `ceo.md` with Guy in roster, QA Routing section, and QA Loop Protocol (3-round limit, vault logging requirement). Updated `CLAUDE.md` hierarchy table. Created vault Code Reference entry and Meeting Notes topic file.
