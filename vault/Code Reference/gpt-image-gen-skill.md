---
title: gpt-image-gen Skill
file: .claude/skills/gpt-image-gen/SKILL.md
type: skill-definition
status: active
created: 2026-05-06
---

## Overview

`gpt-image-gen` is a process skill that wraps the OpenAI Images API. Any agent that needs to produce an image calls this skill with a prompt and an output path; the skill handles the API call, base64 decoding, file save, and verification.

**Design decision:** The skill uses Python for JSON body construction (to safely handle prompts containing quotes or special characters), then pipes through curl. A full Python fallback is provided for environments where jq is unavailable (e.g. Git Bash on Windows).

---

## File Location

`.claude/skills/gpt-image-gen/SKILL.md`

---

## Parameters

| Parameter | Description |
|-----------|-------------|
| `PROMPT` | Complete image generation prompt (plain text) |
| `OUTPUT_PATH` | Destination `.png` file path |

Fixed settings: model `gpt-image-1`, size `1024x1024`, quality `medium`, format `png`.

---

## Key Sections

### Execution Methods
- **Primary (curl + jq):** Python constructs JSON body → curl POSTs → jq extracts b64 → base64 decode → file
- **Fallback (Python end-to-end):** Pure Python using `urllib.request`; no external dependencies beyond Python 3

### Detection Heuristic
```bash
command -v jq >/dev/null 2>&1 && USE_JQ=true || USE_JQ=false
```

### Verification
```bash
[ -s "$OUTPUT_PATH" ] && echo "OK" || echo "FAILED"
```

### Error Handling
- Missing `OPENAI_API_KEY` → stop immediately, report
- API returns `"error"` key → extract `.error.message`, report, do not decode
- Empty/missing output file → report failure with raw response

---

## Dependencies

- `OPENAI_API_KEY` must be set in `.env`
- `curl` required
- `jq` optional (Python 3 fallback covers absence)

---

## Related

[[yuval-agent]] | [[ceo-agent]] | [[env-example]]

---

## Session Log

### 2026-05-06 — Initial skill creation [shipped]
Created as the image generation primitive for the yuval agent. Designed for reuse by any future agent that needs image output. Python-based JSON serialisation chosen to avoid prompt escaping issues in bash.
