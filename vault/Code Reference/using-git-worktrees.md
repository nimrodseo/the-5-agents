---
type: file-reference
file: .claude/skills/using-git-worktrees/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `using-git-worktrees`

> [!info] Skill summary
> **Path:** `.claude/skills/using-git-worktrees/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Sets up an isolated workspace for feature work via `git worktree` — a parallel working directory on a separate branch, so the main checkout stays clean. Falls back to native worktree hooks if outside a git repo.

## When to use

Starting feature work that needs isolation from the current workspace, or before running [[executing-plans]].

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`. See `.claude/skills/using-git-worktrees/`.

## Related skills

- [[executing-plans]] — worktrees are the standard isolation environment for plan execution
- [[finishing-a-development-branch]] — what to do after the worktree's work is done
- [[subagent-driven-development]] — subagents often run inside a worktree
