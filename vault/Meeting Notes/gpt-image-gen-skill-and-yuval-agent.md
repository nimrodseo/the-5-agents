# gpt-image-gen Skill and Yuval Agent

## Overview

Implementation of the image generation capability for the 5-agents system. Two components were added: (1) `gpt-image-gen` — a process skill wrapping the OpenAI Images API with curl+jq primary and Python fallback methods; (2) `yuval` — a creative sub-agent that scans a reference image folder to extract visual style before generating, ensuring visual consistency across all project outputs. The CEO Agent was updated with Yuval's roster entry and image-request routing keywords in Hebrew and English.

## Open Questions

- No OPENAI_API_KEY is set yet — first real image generation will require adding it to `.env`
- `yuval/reference/` is empty; style extraction will be skipped until reference images are dropped in
- Should Yuval support sizes other than 1024×1024 in the future (e.g. portrait/landscape variants)?

## Session Log

### 2026-05-06 — Initial implementation [shipped]
- **What was done:** Created `.claude/skills/gpt-image-gen/SKILL.md` with dual execution methods (curl+jq and Python end-to-end fallback); created `.claude/agents/yuval.md` with 7-step reference-extraction workflow; scaffolded `yuval/reference/` and `yuval/outputs/` directories with `.gitkeep`; added `OPENAI_API_KEY=` to `.env.example`; updated `ceo.md` Agent Roster (Yuval row, Active) and added Image Generation Routing section with Hebrew + English trigger keywords; updated `CLAUDE.md` Agent Hierarchy table; created Code Reference entries for both new artifacts; updated vault indexes.
- **Decisions:** Used Python for JSON body construction in curl command to avoid shell escaping issues with complex prompts. Pure Python fallback chosen over PowerShell for portability (Git Bash on Windows). Yuval's slug derives from first 4 meaningful words of the request for predictable, readable filenames. Sibling `.txt` prompt log is mandatory to enable iteration without re-prompting.
- **Notes / Caveats:** `gpt-image-1` model name used (matching approved plan); update SKILL.md if OpenAI releases a newer model. Yuval cannot view the generated image (no vision loop) — he reports what was requested, not what was produced.
- **Related:** [[ceo-agent-definition]], [[vault-initial-setup]], [[gpt-image-gen-skill]], [[yuval-agent]]
