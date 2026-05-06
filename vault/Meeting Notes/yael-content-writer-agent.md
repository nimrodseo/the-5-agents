# Yael — Content Writer Agent

## Overview

Yael (יעל) is the LLM-only content-writer sub-agent of the 5-agents system. She rewrites raw articles from `Content/` into the project's house style (defined in `yael/style-guide.md` and exemplified by `yael/reference/`), saves the polished result to `Output/`, and copies the original to `Content/Ready/`. She is restricted via the agent's `tools:` frontmatter to `Read, Write, Edit, Glob, Grep` — no Bash, no internet, no API, no agent dispatch. When she identifies a place that needs an illustration, she inserts a `{{IMAGE_NEEDED: "<prompt>"}}` placeholder; the CEO Agent owns the post-processing — parsing placeholders, dispatching Yuval, and stitching the final illustrated article. This embeds the architectural rule that Claude Code sub-agents do not invoke other sub-agents — only the CEO does.

## Open Questions

- `yael/style-guide.md` is a skeleton — the user must fill in the actual house-style rules before Yael's first real run
- `yael/reference/` is empty; until samples are added, Yael works from the style-guide alone
- Yael copies originals to `Content/Ready/` rather than moving them (no Bash → no delete). Consider whether the CEO should clean up `Content/` after a successful run.
- Should the CEO's IMAGE_NEEDED handler save an intermediate "placeholders" version separate from the final illustrated version, or only the final?

## Session Log

### 2026-05-06 — Initial implementation [shipped]
- **What was done:** Created `.claude/agents/yael.md` with `tools: Read, Write, Edit, Glob, Grep` frontmatter (the load-bearing restriction). Scaffolded `yael/style-guide.md` (skeleton for user to fill), `yael/reference/`, `yael/agent.md`. Added project-root flow directories: `Content/`, `Content/Ready/`, `Output/` (all `.gitkeep`-tracked). Updated `ceo.md`: added Yael to the Agent Roster (Active), added the `Content Writing Routing` section with Hebrew + English trigger keywords, added the `IMAGE_NEEDED Placeholder Protocol` section describing the regex-parse → Yuval-dispatch → markdown-replace → save → log flow. Updated `CLAUDE.md` hierarchy table. Removed the `content.md` stub (Yael supersedes it). Created `vault/Code Reference/yael-agent.md` and updated indexes.
- **Decisions:** Restricted tool set chosen to make Yael cheap, deterministic, and unable to take destructive actions. Placeholder format `{{IMAGE_NEEDED: "<prompt>"}}` chosen as a single-line regex-parseable token — easier for the CEO to handle than YAML or HTML comments. Yael copies (not moves) originals because no Bash means no delete; the CEO can prune later if desired. Filename preserved end-to-end (no slugging) so an article's identity is stable across `Content/` → `Output/` → `Content/Ready/`.
- **Notes / Caveats:** `style-guide.md` is empty placeholder text — Yael will refuse to run until the user fills it in (intentional fail-fast). The IMAGE_NEEDED protocol depends on the CEO actually being able to dispatch Yuval as a sub-agent; this works in our system because the CEO is invoked at the top level, not nested.
- **Related:** [[ceo-agent-definition]], [[gpt-image-gen-skill-and-yuval-agent]], [[yael-agent]], [[yuval-agent]], [[ceo-agent]]
