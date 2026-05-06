# Skill-Creator Installation

## Overview

Installation of the official Anthropic `skill-creator` skill into this project at project scope. The skill provides an eval-driven workflow for creating and improving Claude Code skills, including Python eval scripts, subagent graders, and an HTML report viewer. It was installed from `https://github.com/anthropics/skills/tree/main/skills/skill-creator` via the `anthropic-agent-skills` marketplace.

## Open Questions

- The `example-skills@anthropic-agent-skills` plugin bundles 12 skills total; only `skill-creator` was physically installed to `.claude/skills/`. Should the other 11 (`algorithmic-art`, `brand-guidelines`, `canvas-design`, `doc-coauthoring`, `frontend-design`, `internal-comms`, `mcp-builder`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`) be installed too?
- The eval scripts (`scripts/run_eval.py` etc.) require Python. Has Python been set up / tested in this environment?

## Session Log

### 2026-05-06 — Install skill-creator at project scope [shipped]

- **What was done:** Followed the prescribed 3-step CLI sequence. Step 1 (`skill-creator@claude-plugins-official`) found the marketplace but not the plugin. Step 2 was skipped (marketplace was registered). Step 3 — added `anthropics/skills` as a marketplace (`anthropic-agent-skills`), discovered `skill-creator` is bundled inside `example-skills`, manually copied files to `.claude/skills/skill-creator/`, then installed `example-skills@anthropic-agent-skills --scope project` to get official CLI registration. `claude plugin list` confirms `scope: project`.
- **Decisions:** Used `example-skills` parent plugin rather than a non-existent standalone `skill-creator` plugin. Manual copy done first to preserve files independently of the plugin system. Plugin registration creates `.claude/settings.json` with the marketplace source and enabled-plugin entry.
- **Notes / Caveats:** `claude plugin list` tracks CLI-registered plugins only; manually copied skills do not appear there. The `example-skills` bundle includes 11 other skills that were NOT installed to `.claude/skills/` — only skill-creator was copied. `settings.json` is now a tracked project file (committed to git).
- **Related:** [[skill-creator]], [[writing-skills]], [[vault-initial-setup]]
