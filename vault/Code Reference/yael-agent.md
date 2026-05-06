---
title: Yael Agent
file: .claude/agents/yael.md
type: agent-definition
status: active
created: 2026-05-06
---

## Overview

Yael is the content-writer sub-agent — LLM-only by design. She takes raw articles from `Content/`, reads the house-style sources (`yael/style-guide.md` + samples in `yael/reference/`), rewrites the article into the project's voice, and outputs a polished `.md` file to `Output/`. Where an illustration is needed, she inserts a `{{IMAGE_NEEDED: "<prompt>"}}` placeholder rather than generating images herself — image generation is Yuval's job, and the CEO Agent stitches the two together.

**Architecture decision:** Yael is restricted via the `tools:` frontmatter field to `Read, Write, Edit, Glob, Grep`. No Bash, no WebSearch, no API access, no Agent dispatch. This makes her cheap, deterministic, and safe to invoke autonomously. The cross-agent flow with Yuval is mediated entirely through the CEO via the placeholder protocol — Claude Code sub-agents do not invoke other sub-agents.

Yael replaces the previously-planned `content.md` stub. The original stub was deleted in this commit; Yael narrows the scope from "general long-form content" to "rewrite-in-house-style" — a more concrete responsibility.

---

## File Location

`.claude/agents/yael.md`

---

## Tool Restrictions

```yaml
tools: Read, Write, Edit, Glob, Grep
```

This is the load-bearing line. It enforces:
- No shell access (cannot run scripts, cannot delete files)
- No internet access (cannot fetch sources, cannot verify facts online)
- No agent dispatch (cannot call Yuval, cannot escalate)

If Yael needs something outside these tools, she returns a status to the CEO and the CEO decides.

---

## Working Directory

`yael/` at project root:

| Path | Purpose |
|------|---------|
| `yael/style-guide.md` | House-style rules; read at the start of every task |
| `yael/reference/` | Sample articles in our voice; read at the start of every task |
| `yael/agent.md` | Human-readable pointer to `.claude/agents/yael.md` |

Plus the article-flow directories at project root:

| Path | Purpose |
|------|---------|
| `Content/` | Raw articles awaiting rewrite |
| `Content/Ready/` | Originals that have been processed (Yael copies, doesn't delete — no Bash) |
| `Output/` | Final rewritten articles |

---

## Workflow (7 Steps)

1. Pull article from `Content/` (named file, or most recent)
2. Read `yael/style-guide.md` and Glob+Read every file in `yael/reference/`
3. Rewrite in house style
4. Insert `{{IMAGE_NEEDED: "<prompt>"}}` placeholders where illustrations are needed
5. Save to `Output/<original-filename>.md` with frontmatter (source, processed_by, processed_date, image_placeholders count)
6. Copy original to `Content/Ready/<original-filename>` (no delete — Yael has no Bash)
7. Report: output path, placeholder list, style-change summary

---

## IMAGE_NEEDED Protocol

Yael's only handoff to Yuval is the placeholder. The CEO parses these via regex:

```
\{\{IMAGE_NEEDED:\s*"([^"]+)"\}\}
```

For each match, the CEO dispatches Yuval with the captured prompt and replaces the placeholder with a markdown image reference. See `.claude/agents/ceo.md` → "IMAGE_NEEDED Placeholder Protocol" for the full CEO-side procedure.

---

## Trigger Keywords

**Hebrew:** שכתב, ערוך, נסח מחדש, תרגם, סכם, מאמר, תוכן, פוסט

**English:** rewrite, edit, rephrase, translate, summarize, article, content, post

---

## Dependencies

- `yael/style-guide.md` — must exist; Yael stops if missing
- `Content/` directory — input source

No API keys, no external services.

---

## Related

[[ceo-agent]] | [[yuval-agent]] | [[gpt-image-gen-skill]]

---

## Session Log

### 2026-05-06 — Initial agent creation [shipped]
Created `yael.md` with restricted tool set (Read/Write/Edit/Glob/Grep). Scaffolded `yael/style-guide.md` (skeleton for user to fill), `yael/reference/`, `yael/agent.md`. Added project-root scaffolds: `Content/`, `Content/Ready/`, `Output/`. Updated CEO agent with content-writing routing keywords and the IMAGE_NEEDED Placeholder Protocol that mediates Yael→Yuval handoff. Removed the `content.md` stub — Yael supersedes it. Updated CLAUDE.md hierarchy table.
