---
type: file-reference
file: .claude/skills/subagent-driven-development/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `subagent-driven-development`

> [!info] Skill summary
> **Path:** `.claude/skills/subagent-driven-development/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Pattern for driving multi-step implementation plans via subagents **within the current session** — as opposed to [[dispatching-parallel-agents]] (parallel, stateless) or [[executing-plans]] (new isolated session). Each subagent handles one chunk; a reviewer subagent checks quality between chunks.

## When to use

Executing implementation plans where tasks are mostly sequential and inter-dependent, and you want to keep everything in one session.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`, `implementer-prompt.md`, `spec-reviewer-prompt.md`, `code-quality-reviewer-prompt.md`. See `.claude/skills/subagent-driven-development/`.

## Related skills

- [[dispatching-parallel-agents]] — parallel variant (no dependencies)
- [[executing-plans]] — variant in isolated fresh session
- [[writing-plans]] — produces the plan input
- [[verification-before-completion]] — final gate
