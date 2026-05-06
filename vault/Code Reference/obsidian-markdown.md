---
type: file-reference
file: .claude/skills/obsidian-markdown/
component: skill
upstream: user-installed (Obsidian skills bundle)
tags:
  - file-reference
  - skill
  - obsidian
---

# Skill: `obsidian-markdown`

> [!info] Skill summary
> **Path:** `.claude/skills/obsidian-markdown/`
> **Source:** added by the user (separate install — not from `obra/superpowers`)
> **Entry point:** `SKILL.md`

## What

Reference for Obsidian-flavored markdown extensions over CommonMark / GFM: wikilinks (`[[Note]]`), embeds (`![[Note]]`), callouts (`> [!note]`), properties (frontmatter), tags, comments (`%%hidden%%`), highlights (`==text==`), Mermaid diagrams, math, footnotes.

## When to use

Authoring or editing `.md` files inside an Obsidian vault; user mentions wikilinks, callouts, frontmatter, tags, embeds, or Obsidian notes. The vault docs in this project are themselves Obsidian-flavored, so this skill is invoked indirectly any time vault files are touched.

## Belongs to

Installed manually by the user as part of an Obsidian-skills bundle (alongside [[obsidian-bases]] and [[obsidian-vault-workflow]]).

## Internal files

Just `SKILL.md`. See `.claude/skills/obsidian-markdown/`. The skill itself references additional doc files (`references/PROPERTIES.md`, `references/EMBEDS.md`, `references/CALLOUTS.md`) that are NOT yet present locally.

## Related skills

- [[obsidian-vault-workflow]] — uses this skill's syntax for every vault note
- [[obsidian-bases]] — sibling Obsidian skill
