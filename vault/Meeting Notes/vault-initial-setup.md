# Vault Initial Setup

## Overview

The `vault/` directory is the long-term memory for the the-5-agents project, structured per the `obsidian-vault-workflow` skill. It contains five sub-folders: `Code Reference/` (one doc per project artifact), `Meeting Notes/` (topical session logs for code and architecture), `Content Briefs/` (editorial specs), `Publishing Log/` (publish-run records), and `Brand Guidelines/` (voice, tone, visuals). Each folder maintains a flat `_index.md` listing all topics inside it. All docs use Obsidian-flavored markdown with wikilinks for cross-referencing.

## Open Questions

- Will agent-definition files (under `.claude/agents/`) receive their own Code Reference entries once agents are defined? Likely yes — add a new section to [[Code Reference/_index]] at that time.
- Should the three new Obsidian skills (`obsidian-bases`, `obsidian-markdown`, `obsidian-vault-workflow`) be committed/pushed to GitHub? They are currently untracked (git status shows `?? .claude/skills/obsidian-*`).
- Should `.gitignore` be updated to exclude `.obsidian/` (Obsidian config folder at project root)?

## Session Log

### 2026-05-06 — Vault skeleton + all Code Reference docs [shipped]

- **What was done:** Created the full `vault/` folder structure (`Code Reference/`, `Meeting Notes/`, `Content Briefs/`, `Publishing Log/`, `Brand Guidelines/`) with `_index.md` in each folder. Wrote 21 Code Reference entries — 4 for top-level project files (`CLAUDE.md`, `.env`, `.env.example`, `.gitignore`) and 17 for every installed skill. Updated `CLAUDE.md` to mandate the vault workflow at the top. Saved a persistent memory entry for the cross-session "always invoke obsidian-vault-workflow" preference.
- **Decisions:** Documented skills at the skill level (one doc per skill folder, not one per internal file) — the skills' own `SKILL.md` files already document their internals. Created a `Code Reference/` folder that is not part of the standard four vault folders but is justified by the per-file reference-doc need. Used Obsidian-flavored frontmatter and callouts throughout.
- **Notes / Caveats:** Three new Obsidian skills were user-installed after the Superpowers install (they were untracked in git). The `vault/` folder itself is also untracked. All of this needs a separate commit+push. The `obsidian-markdown` SKILL.md references helper files (`references/PROPERTIES.md`, `references/EMBEDS.md`, `references/CALLOUTS.md`) that do not yet exist locally — these may need to be sourced if the skill is used heavily.
- **Related:** [[obsidian-vault-workflow]], [[claude-md]], [[Code Reference/_index]]
