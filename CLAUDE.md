# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Mandatory Workflow — Obsidian Vault

**Before** any task in this project (coding, content, design, architecture, bugfix, review, refactor) — **and again at the end** — you MUST follow the protocol defined in [`.claude/skills/obsidian-vault-workflow/SKILL.md`](.claude/skills/obsidian-vault-workflow/SKILL.md).

In short:

- **Phase 1 (start):** name the topic, locate / read its file under `vault/` (Meeting Notes / Content Briefs / Publishing Log / Brand Guidelines), plus 2–3 recent Meeting Notes and any matching Content Briefs / Brand Guidelines. Report what you loaded in one sentence.
- **Phase 2 (end):** append `### YYYY-MM-DD — <title> [status]` at the bottom of the topic file's `## Session Log`, update Overview if scope/status changed, maintain `## Open Questions`, include `**Related:** [[wikilinks]]`, and add the topic line to the folder's `_index.md` if new. Read back to verify.

Per-file reference docs live under [`vault/Code Reference/`](vault/Code%20Reference/) — read the relevant entry there if your task touches a specific file.

Skip only for purely informational Q&A that touches zero files and produces zero decisions.

## Project Overview

**the-5-agents** הוא פרויקט של צוות סוכנים ליצירת תוכן.
המבנה מבוסס על סוכן ראשי (מנכ"ל) שמנהל ומתזמן צוות של סוכנים נוספים, כל אחד עם תפקיד ייעודי בתהליך יצירת התוכן.

זהותם, התפקידים והאינטראקציות בין הסוכנים יוגדרו בהמשך ויתווספו לקובץ הזה כשהמבנה יתגבש.

## Agent Hierarchy

The system uses a single orchestration layer. All agent definitions live under `.claude/agents/`.

| Agent | File | Role | Status |
|---|---|---|---|
| CEO | `.claude/agents/ceo.md` | Orchestration — sole entry point, dispatches all sub-agents | **Active** |
| Yuval | `.claude/agents/yuval.md` | Creative image generation | **Active** |
| Yael | `.claude/agents/yael.md` | Content rewriting in house style | **Active** |
| Chen | `.claude/agents/chen.md` | Web research; deposits findings in Content/ for Yael | **Active** |
| Guy | `.claude/agents/guy.md` | QA gatekeeper; final approval before output reaches user | **Active** |

To invoke the CEO Agent, dispatch it via Task with the task description. The CEO handles routing to sub-agents internally. Sub-agents marked "Planned" are stubbed with defined interfaces but not yet implemented.

## Project Structure

תחת התיקייה `.claude/` בשורש הפרויקט יושבים רכיבים מותאמים אישית עבור הפרויקט:

- **`.claude/agents/`** — הגדרות ה-subagents של הצוות (המנכ"ל + הסוכנים שתחתיו)
- **`.claude/skills/`** — skills מותאמים שיהיו זמינים לסוכנים
- **`.claude/commands/`** — slash commands מותאמים לפרויקט

## Status

הפרויקט בשלב הקמה ראשוני — אין עדיין קוד, תלויות, או פקודות build/test/run.
קובץ זה יורחב עם פקודות, ארכיטקטורה ופרטי תהליך עבודה ככל שיתווספו רכיבים לפרויקט.
