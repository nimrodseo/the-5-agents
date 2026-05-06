---
type: file-reference
file: .claude/skills/using-superpowers/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
  - meta
---

# Skill: `using-superpowers`

> [!info] Skill summary
> **Path:** `.claude/skills/using-superpowers/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

The **meta-skill** — establishes that Claude must invoke the Skill tool (not just recall knowledge) before any response in any conversation, including clarifying questions. Describes how to discover, read, and invoke every other skill in `.claude/skills/`.

## When to use

At the start of every conversation. It is the "bootstrap" — once active, it surfaces all other skills as needed.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md` plus `references/codex-tools.md`, `references/copilot-tools.md`, `references/gemini-tools.md` — cross-platform tool reference sheets for AI agents running in different environments.

## Related skills

- All other installed skills — this skill points Claude toward them
- [[obsidian-vault-workflow]] — also a start-of-session requirement, co-invoked with this one
