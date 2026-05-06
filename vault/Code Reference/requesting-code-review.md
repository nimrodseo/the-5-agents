---
type: file-reference
file: .claude/skills/requesting-code-review/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `requesting-code-review`

> [!info] Skill summary
> **Path:** `.claude/skills/requesting-code-review/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Pattern for invoking a code-review subagent (or human reviewer) on a completed change — verifies that the work meets requirements before merging or finalizing.

## When to use

When completing tasks, implementing major features, or before merge / PR.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md` plus `code-reviewer.md` (the reviewer-subagent prompt). See `.claude/skills/requesting-code-review/`.

## Related skills

- [[receiving-code-review]] — paired sibling (handles the response side)
- [[finishing-a-development-branch]] — typical step right after this
- [[verification-before-completion]] — runs in parallel with review
