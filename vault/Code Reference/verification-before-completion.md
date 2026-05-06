---
type: file-reference
file: .claude/skills/verification-before-completion/
component: skill
upstream: obra/superpowers
tags:
  - file-reference
  - skill
---

# Skill: `verification-before-completion`

> [!info] Skill summary
> **Path:** `.claude/skills/verification-before-completion/`
> **Source:** [obra/superpowers](https://github.com/obra/superpowers)
> **Entry point:** `SKILL.md`

## What

Requires running real verification commands and confirming their output **before** claiming work is complete, tests pass, or a fix is done. Evidence before assertions — no claiming "done" based on code reading alone.

## When to use

Right before claiming work is complete, fixed, or passing, and before committing or creating PRs.

## Belongs to

Installed via the manual install of the [[using-superpowers|Superpowers]] plugin (`obra/superpowers`).

## Internal files

`SKILL.md`. See `.claude/skills/verification-before-completion/`.

## Related skills

- [[finishing-a-development-branch]] — verification is the gate before this
- [[requesting-code-review]] — both run at the "about to ship" checkpoint
- [[test-driven-development]] — tests are the primary verification artifact
- [[systematic-debugging]] — debugging often surfaces the need to re-verify
