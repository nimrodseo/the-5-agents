---
type: file-reference
file: .claude/skills/receiving-code-review/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `receiving-code-review`

> [!info] Skill summary
> **Path:** `.claude/skills/receiving-code-review/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Discipline for handling incoming code-review feedback rigorously — verify each point against the actual code before agreeing or implementing, especially when feedback is unclear or technically questionable. Counters performative-agreement and blind-implementation failure modes.

## When to use

Any time review feedback arrives (from a human, another agent, or [[requesting-code-review]]) and before acting on it.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`. See `.claude/skills/receiving-code-review/`.

## Related skills

- [[requesting-code-review]] — paired sibling (the other side of the loop)
- [[systematic-debugging]] — invoked when feedback identifies a bug to verify
- [[verification-before-completion]] — used to confirm fixes after applying feedback
