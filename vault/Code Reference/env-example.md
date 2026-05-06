---
type: file-reference
file: .env.example
component: project-root
gitignored: false
tags:
  - file-reference
  - root
  - template
---

# `.env.example`

> [!info] Public template — safe to commit
> **Path:** `.env.example`
> **Component:** project root
> **Status:** committed to the repo

## What

Template documenting which environment variables `.env` should define. Carries variable names + comments only — **no real values**. New contributors copy this to `.env` and fill in their own credentials.

Currently lists:

- `ANTHROPIC_API_KEY` — Claude API key (only needed for direct SDK use, not Claude Code CLI)
- `PROJECT_NAME` / `PROJECT_ENV` — basic project metadata
- Commented placeholders for additional service keys to uncomment when needed (e.g. `OPENAI_API_KEY`, `GOOGLE_API_KEY`, `SERPER_API_KEY`)

## Belongs to

Repository — committed and tracked. Updated alongside [[env]] whenever new environment variables are introduced, so the template stays in sync.

## Related

- [[env]] — local-secret counterpart
- [[gitignore]] — defines that `.env` (but not `.env.example`) is excluded
- [[claude-md]] — project root sibling
