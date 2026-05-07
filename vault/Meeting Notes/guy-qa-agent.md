# Guy — QA Agent

## Overview

Guy (גיא) is the 5th and final active sub-agent in the 5-agents content pipeline. He is the Quality Assurance gatekeeper — nothing reaches the user without his ✅. The CEO activates him automatically at the end of every content pipeline after Yael delivers the final output (with images integrated). Guy reads the output, runs a structured 5-category checklist, writes a QA report to `guy/QA_Reports/`, and returns a pass/fail verdict to the CEO.

Guy cannot fix content — his tools are `Read, Glob, Grep, Write` (Write only for creating new report files). If he fails an output, the CEO re-briefs Yael with Guy's correction notes and returns the revised output for re-review. Maximum 3 rounds; on round 3 failure the CEO escalates to the user with the QA report.

Pipeline: `CEO → Chen → CEO → Yael → CEO → Yuval → CEO → Yael (final) → CEO → Guy → CEO → User`

## Open Questions

- Should Guy have a configurable checklist (per-project type or per-content-type), or is the fixed 5-category checklist permanent across all runs?
- Should QA reports in `guy/QA_Reports/` be pruned after N days, or kept indefinitely as an audit trail?
- Should Guy score each checklist category numerically (e.g. 1–5) in addition to pass/fail, to enable trend analysis over time?

## Session Log

### 2026-05-07 — Initial implementation [shipped]
- **What was done:** Created `.claude/agents/guy.md` with `tools: Read, Glob, Grep, Write` frontmatter (no Edit — the load-bearing restriction). Scaffolded `guy/QA_Reports/` (tracked via `.gitkeep`) and `guy/agent.md` (human pointer). Updated `ceo.md`: added Guy to Agent Roster (Active), added QA Routing section with Hebrew + English trigger keywords + note that Guy runs automatically at end of every pipeline, added QA Loop Protocol section (3-round limit, Yael re-brief flow, round-3 escalation to user, vault logging requirement per pass). Updated `CLAUDE.md` hierarchy table. Created `vault/Code Reference/guy-agent.md` and updated both vault `_index.md` files.
- **Decisions:** `tools: Read, Glob, Grep, Write` without Edit chosen to make Guy's authority read-only on all existing files — he can only create new report files. This prevents him from accidentally modifying outputs. Write permission is intentionally not scoped (Claude Code frontmatter doesn't support directory scoping) — the instructions constrain usage. 3-round limit chosen to prevent infinite correction loops; human escalation on round 3 keeps the user in control of edge cases. Guy runs automatically (not keyword-triggered) at pipeline end, so no explicit user instruction is needed.
- **Notes / Caveats:** QA checklist category 4 (תמונות) is "not applicable" when the output has no images — Guy should skip it cleanly rather than fail. `yael/style-guide.md` is currently a skeleton; style checks will be weak until the user fills it in. This was already a known open question from the Yael session.
- **Related:** [[ceo-agent]], [[yael-agent]], [[chen-agent]], [[yuval-agent]], [[guy-agent]]
