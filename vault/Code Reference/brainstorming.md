---
type: file-reference
file: .claude/skills/brainstorming/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `brainstorming`

> [!info] Skill summary
> **Path:** `.claude/skills/brainstorming/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Forces Claude to explore user intent, requirements, and design **before any implementation**. Use before creating features, building components, adding functionality, or modifying behavior — surfaces ambiguity early instead of mid-implementation.

## When to use

Any creative or implementation task — features, components, behavioral changes. Required *before* code, not after the fact.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

Includes `SKILL.md`, `spec-document-reviewer-prompt.md`, `visual-companion.md`, plus a `scripts/` folder (`frame-template.html`, `helper.js`, `server.cjs`, `start-server.sh`, `stop-server.sh`) for an interactive brainstorming UI. See `.claude/skills/brainstorming/` for the full inventory.

## Related skills

- [[writing-plans]] — natural follow-on once intent is clear
- [[writing-skills]] — when the brainstorm output is itself a new skill
- [[using-superpowers]] — the meta-skill that surfaces this one
