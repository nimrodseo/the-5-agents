---
title: Yuval Agent
file: .claude/agents/yuval.md
type: agent-definition
status: active
created: 2026-05-06
---

## Overview

Yuval is the creative image agent — the only agent in the system that produces visual assets. He is defined as a Claude Code sub-agent at `.claude/agents/yuval.md` and dispatched via the CEO Agent on image-related requests. His distinguishing feature is a reference-based style extraction workflow: before every generation he scans `yuval/reference/` for inspiration images and derives a consistent visual language to apply to the prompt.

---

## File Location

`.claude/agents/yuval.md`

---

## Working Directory

`yuval/` at project root:

| Path | Purpose |
|------|---------|
| `yuval/reference/` | Drop inspiration images here; Yuval reads them before every generation |
| `yuval/outputs/` | Generated PNGs land here, named `YYYY-MM-DD-<slug>.png` |
| `yuval/agent.md` | Human-readable pointer to `.claude/agents/yuval.md` |
| `yuval/skill.md` | Human-readable pointer to `.claude/skills/gpt-image-gen/SKILL.md` |

---

## Workflow (7 Steps)

1. Scan `yuval/reference/` — read images, extract style (colors, motifs, composition, mood)
2. Select relevant style elements for this request
3. Compose prompt: user intent + extracted style (2–4 sentences)
4. Call `gpt-image-gen` skill → save to `yuval/outputs/YYYY-MM-DD-<slug>.png`
5. Write sibling `.txt` with exact prompt used
6. Verify output file exists and is non-empty
7. Report: path, prompt, references used, verification status

---

## Trigger Keywords

**Hebrew:** תמונה של, ציור של, צור תמונה, עצב לי, תמונת רקע, פוסטר, באנר, ויזואל, אייקון, לוגו

**English:** generate image, create image, design a, make a poster, make a banner, visual for, illustration of, draw a, image of, artwork for, thumbnail, hero image, icon, logo

---

## Dependencies

- `.claude/skills/gpt-image-gen/SKILL.md` — image generation primitive
- `OPENAI_API_KEY` in `.env`

---

## Related

[[gpt-image-gen-skill]] | [[ceo-agent]] | [[env-example]]

---

## Session Log

### 2026-05-06 — Initial agent creation [shipped]
Created yuval.md with 7-step workflow, working directory scaffold (yuval/reference/, yuval/outputs/), and pointer docs. Added to CEO agent roster and CLAUDE.md hierarchy table. CEO Image Generation Routing section added to route Hebrew and English image-request keywords to Yuval.
