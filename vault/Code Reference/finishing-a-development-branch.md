---
type: file-reference
file: .claude/skills/finishing-a-development-branch/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `finishing-a-development-branch`

> [!info] Skill summary
> **Path:** `.claude/skills/finishing-a-development-branch/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Decision-tree skill: presents structured options for integrating completed work — direct merge, opening a PR, abandoning the branch, or further cleanup. Invokes once tests pass and the implementation feels done.

## When to use

After implementation is complete and verification has passed — but before the branch is merged or a PR is opened.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

Just `SKILL.md`. See `.claude/skills/finishing-a-development-branch/`.

## Related skills

- [[verification-before-completion]] — must run first
- [[requesting-code-review]] — typical step before opening PR
- [[using-git-worktrees]] — informs how the branch was set up
