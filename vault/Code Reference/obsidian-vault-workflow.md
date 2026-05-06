---
type: file-reference
file: .claude/skills/obsidian-vault-workflow/
component: skill
upstream: user-installed (Obsidian skills bundle)
tags:
  - file-reference
  - skill
  - obsidian
  - mandatory
---

# Skill: `obsidian-vault-workflow`

> [!important] Mandatory for every task
> **Path:** `.claude/skills/obsidian-vault-workflow/`
> **Source:** added by the user
> **Entry point:** `SKILL.md`

## What

The protocol that turns the `vault/` folder into Claude's persistent project memory. Two phases:

- **Phase 1 (start)** — identify the topic, read the matching `vault/` topic file fully (Overview + Open Questions + every Session Log entry), plus 2–3 most recent Meeting Notes and any matching Content Briefs / Brand Guidelines. Report what was loaded in one sentence.
- **Phase 2 (end)** — append `### YYYY-MM-DD — <title> [status]` at the bottom of `## Session Log`, update Overview if scope or status changed, maintain `## Open Questions`, include `**Related:** [[wikilinks]]`, add a topic line to the folder `_index.md` if new, then read the file back to verify.

The skill defines folder conventions (`Meeting Notes/`, `Content Briefs/`, `Publishing Log/`, `Brand Guidelines/`), filename rules (lowercase-hyphenated, no date), session-status tags (`shipped`, `wip`, `spiked`, `reverted`, `planned`, `debug`), and a long anti-pattern list.

## When to use

**Every task.** Coding, content, architecture, UI, bugfix, review, refactor — anything that touches files or produces decisions. Skip only for purely informational Q&A.

## Belongs to

Installed manually by the user as part of an Obsidian-skills bundle. This project's [[claude-md|CLAUDE.md]] mandates it at the top.

## Internal files

Just `SKILL.md`. See `.claude/skills/obsidian-vault-workflow/`.

## Related skills

- [[obsidian-markdown]] — formatting for every note this skill produces
- [[obsidian-bases]] — sibling (database views over the vault)
- [[using-superpowers]] — the meta-skill — vault-workflow is itself one of the skills it surfaces
