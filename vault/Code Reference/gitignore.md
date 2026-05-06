---
type: file-reference
file: .gitignore
component: project-root
tags:
  - file-reference
  - root
---

# `.gitignore`

> [!info] File reference
> **Path:** `.gitignore`
> **Component:** project root

## What

Tracked exclusion list. Primary purpose: prevent `.env` (real secrets) from ever being committed. Also excludes common OS/editor noise and dependency directories that may appear later.

Current rules cover:

- **Secrets:** `.env`, `.env.local`, `.env.*.local`
- **OS:** `.DS_Store`, `Thumbs.db`
- **Editors:** `.vscode/`, `.idea/`, `*.swp`
- **Logs:** `*.log`
- **Dependencies (forward-looking):** `node_modules/`, `__pycache__/`, `*.pyc`, `.venv/`, `venv/`

## Belongs to

Repository — committed alongside [[env-example]] from the very first commit so secrets can never accidentally land on `origin/main`.

## Related

- [[env]] — the file this most critically protects
- [[env-example]] — committed template (explicitly NOT excluded)
- [[claude-md]] — project root sibling
