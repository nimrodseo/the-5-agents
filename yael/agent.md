# Yael — Agent Pointer

Yael's canonical agent definition lives at `.claude/agents/yael.md`.

This folder (`yael/`) is her working directory:

| Path | Purpose |
|------|---------|
| `style-guide.md` | The house-style rules. Yael reads this at the start of every task. |
| `reference/` | Drop sample articles in our voice here. Yael reads them to internalize tone through examples. |

Yael is LLM-only — Read, Write, Edit, Glob, Grep. No Bash, no internet, no API access, no agent dispatch.

To invoke Yael, ask the CEO Agent for a rewrite (or use trigger keywords like "שכתב", "rewrite", "edit", "מאמר", etc.).

When Yael identifies a place in the article that needs an image, she leaves a `{{IMAGE_NEEDED: "<prompt>"}}` placeholder. The CEO Agent picks up these placeholders, dispatches Yuval to generate the images, and stitches the final illustrated article into `Output/`.
