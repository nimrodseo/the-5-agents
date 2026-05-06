---
type: file-reference
file: .env
component: project-root
gitignored: true
tags:
  - file-reference
  - root
  - secrets
---

# `.env`

> [!warning] Local-only — never commit
> **Path:** `.env`
> **Component:** project root
> **Status:** gitignored — holds real secrets
> **Owner:** local developer machine only

## What

Local environment file holding **real** secrets used by the project (e.g. `ANTHROPIC_API_KEY`). Currently empty / placeholder values — to be populated by the developer.

The file is excluded from git via [[gitignore]] line `.env`. `git check-ignore -v .env` confirms the rule applies.

## Belongs to

Local developer machine. Each contributor maintains their own `.env`; never share its contents in chat, commit, or any external system.

## Related

- [[env-example]] — public template that mirrors the variable names
- [[gitignore]] — enforces the exclusion
- [[claude-md]] — project root sibling
