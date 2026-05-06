---
type: file-reference
file: .claude/skills/executing-plans/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `executing-plans`

> [!info] Skill summary
> **Path:** `.claude/skills/executing-plans/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Procedure for executing a written implementation plan in a fresh session, with review checkpoints between phases. Pairs with [[writing-plans]] (which produces the plan) and [[verification-before-completion]] (which gates the "done" claim).

## When to use

You have a finalized plan document and want to execute it cleanly — typically in a worktree, with reviewer subagents at checkpoints.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

Just `SKILL.md`. See `.claude/skills/executing-plans/`.

## Related skills

- [[writing-plans]] — produces the input
- [[using-git-worktrees]] — typical isolation strategy
- [[subagent-driven-development]] — common execution pattern
- [[verification-before-completion]] — final gate
- [[finishing-a-development-branch]] — what to do after execution succeeds
