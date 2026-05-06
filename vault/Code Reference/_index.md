---
title: Code Reference — Index
type: folder-index
tags:
  - index
  - file-reference
---

# Code Reference — Index

One markdown note per project artifact (top-level config files, installed skills). Each entry describes **what** the artifact does, **who** owns / authored it, and links to **related** artifacts.

## Topics

### Project root

- [[claude-md]] — Project-level Claude Code instructions (mandatory workflow + overview)
- [[env]] — Local-only secrets file (gitignored)
- [[env-example]] — Committed template showing what variables `.env` should contain
- [[gitignore]] — Tracked exclusions, primarily protecting `.env`

### Skills (under `.claude/skills/`)

- [[brainstorming]] — Explore user intent before any creative/implementation work
- [[dispatching-parallel-agents]] — Run 2+ independent tasks in parallel agents
- [[executing-plans]] — Execute a written plan with review checkpoints in a separate session
- [[finishing-a-development-branch]] — Decide how to integrate completed work (merge/PR/cleanup)
- [[obsidian-bases]] — Author Obsidian `.base` files (table/card views, filters, formulas)
- [[obsidian-markdown]] — Author Obsidian-flavored markdown (wikilinks, embeds, callouts)
- [[obsidian-vault-workflow]] — Mandatory vault read/write protocol — start & end of every task
- [[receiving-code-review]] — Verify and respond rigorously to code-review feedback
- [[requesting-code-review]] — Run a code-review subagent before merging major work
- [[subagent-driven-development]] — Drive multi-step plans via subagents in current session
- [[systematic-debugging]] — Diagnose bugs / test failures before proposing fixes
- [[test-driven-development]] — Write tests before implementation
- [[using-git-worktrees]] — Isolate feature work in a worktree before plan execution
- [[using-superpowers]] — Meta-skill — invoke Skill tool before responding in any conversation
- [[verification-before-completion]] — Run real verification commands before claiming "done"
- [[writing-plans]] — Author implementation plans before touching code
- [[writing-skills]] — Create / edit / verify skills before deployment
- [[skill-creator]] — Official Anthropic skill for creating, eval-ing, and optimizing skills (project-scoped plugin)

### Skills (project-custom, under `.claude/skills/`)

- [[gpt-image-gen-skill]] — OpenAI Images API wrapper; generates PNG from prompt; used by yuval agent

### Agents (under `.claude/agents/`)

- [[ceo-agent]] — CEO Agent: sole orchestration layer, dispatches and monitors all sub-agents (active)
- [[yuval-agent]] — Yuval: creative image agent; reference-based style extraction + gpt-image-gen (active)
- [[yael-agent]] — Yael: content writer; LLM-only, rewrites Content/ → Output/ with IMAGE_NEEDED placeholders (active)
- [[chen-agent]] — Chen: web research agent; memory-checked searches, deposits findings in Content/ (active)
- Marketing Agent — `.claude/agents/marketing.md` — planned, not yet implemented
- Sales Agent — `.claude/agents/sales.md` — planned, not yet implemented
- Dev Agent — `.claude/agents/dev.md` — planned, not yet implemented
