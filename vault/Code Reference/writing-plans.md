---
type: file-reference
file: .claude/skills/writing-plans/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `writing-plans`

> [!info] Skill summary
> **Path:** `.claude/skills/writing-plans/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Structures implementation planning before touching code — produces a plan document with phased tasks, acceptance criteria, and risk notes. Prevents scope creep and mid-implementation pivots by settling design upfront.

## When to use

When you have a spec or requirements for a multi-step task, before touching code.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`, `plan-document-reviewer-prompt.md`. See `.claude/skills/writing-plans/`.

## Related skills

- [[brainstorming]] — natural precursor to planning
- [[executing-plans]] — consumes the plan this skill produces
- [[subagent-driven-development]] — an execution pattern for the resulting plan
- [[writing-skills]] — if the plan is for building a new skill
