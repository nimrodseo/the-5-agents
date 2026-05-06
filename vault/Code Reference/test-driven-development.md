---
type: file-reference
file: .claude/skills/test-driven-development/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `test-driven-development`

> [!info] Skill summary
> **Path:** `.claude/skills/test-driven-development/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Red-green-refactor TDD discipline — write a failing test first, then write only enough code to pass it, then refactor. Includes anti-patterns to avoid (mocking too aggressively, writing tests after, ignoring test feedback).

## When to use

Before writing any implementation code for a feature or bugfix.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`, `testing-anti-patterns.md`. See `.claude/skills/test-driven-development/`.

## Related skills

- [[systematic-debugging]] — companion when a test reveals a bug
- [[verification-before-completion]] — confirms tests actually pass before claiming done
- [[writing-plans]] — TDD cycles are often specified in plans
