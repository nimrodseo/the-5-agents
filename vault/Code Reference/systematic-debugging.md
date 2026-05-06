---
type: file-reference
file: .claude/skills/systematic-debugging/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `systematic-debugging`

> [!info] Skill summary
> **Path:** `.claude/skills/systematic-debugging/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Structured methodology for diagnosing bugs, test failures, and unexpected behavior **before proposing any fix** — requires forming a hypothesis, gathering evidence, confirming root cause, and only then writing a fix. Counters the "guess-and-patch" anti-pattern.

## When to use

Any bug, test failure, or unexpected behavior — before touching code.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`, `CREATION-LOG.md`, `condition-based-waiting.md`, `condition-based-waiting-example.ts`, `defense-in-depth.md`, `find-polluter.sh`, `root-cause-tracing.md`, `test-academic.md`, `test-pressure-1.md`, `test-pressure-2.md`, `test-pressure-3.md`. See `.claude/skills/systematic-debugging/`.

## Related skills

- [[test-driven-development]] — companion for reproducing bugs as tests first
- [[verification-before-completion]] — confirms the fix is real
- [[receiving-code-review]] — often surfaces issues this skill then diagnoses
