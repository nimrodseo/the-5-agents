---
type: file-reference
file: .claude/skills/dispatching-parallel-agents/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `dispatching-parallel-agents`

> [!info] Skill summary
> **Path:** `.claude/skills/dispatching-parallel-agents/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Pattern for dispatching 2+ independent tasks to parallel agents — when subtasks share no state and have no sequential dependency, fan them out instead of running sequentially.

## When to use

Multiple genuinely independent pieces of work in a single turn (e.g. several searches, several edits in different files, several review questions).

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

Just `SKILL.md`. See `.claude/skills/dispatching-parallel-agents/`.

## Related skills

- [[subagent-driven-development]] — sibling pattern for sequential subagent use
- [[executing-plans]] — plans often produce parallelizable steps
- [[using-superpowers]] — the meta-skill
