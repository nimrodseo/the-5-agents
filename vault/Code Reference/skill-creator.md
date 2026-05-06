---
type: file-reference
file: .claude/skills/skill-creator/
component: skill
upstream: anthropics/skills (example-skills plugin)
registered-plugin: example-skills@anthropic-agent-skills
tags:
  - file-reference
  - skill
  - anthropic-official
---

# Skill: `skill-creator`

> [!info] Skill summary
> **Path:** `.claude/skills/skill-creator/`
> **Source:** [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/skill-creator)
> **Registered as:** `example-skills@anthropic-agent-skills` (scope: project)
> **Entry point:** `SKILL.md`

## What

Official Anthropic skill for **creating, editing, optimizing, and evaluating Claude Code skills**. Provides an end-to-end workflow: describe the new skill → generate a `SKILL.md` → run evals against benchmark prompts → grade with subagents → iterate based on scores. Includes eval infrastructure (Python scripts, HTML viewer, agent prompts for analysis, comparison, and grading).

## When to use

- Creating a new skill from scratch
- Editing or improving an existing skill's prompt
- Measuring skill performance with variance analysis
- Optimizing a skill's trigger description for accuracy
- Running evals to test before deploying a skill

## Belongs to

Installed from the official Anthropic skills repository. Registered at **project scope** via the `example-skills@anthropic-agent-skills` plugin (declared in `.claude/settings.json`).

## Internal files

`SKILL.md`, `LICENSE.txt`, `agents/analyzer.md`, `agents/comparator.md`, `agents/grader.md`, `references/schemas.md`, `scripts/run_eval.py`, `scripts/run_loop.py`, `scripts/aggregate_benchmark.py`, `scripts/generate_report.py`, `scripts/improve_description.py`, `scripts/package_skill.py`, `scripts/quick_validate.py`, `scripts/utils.py`, `eval-viewer/viewer.html`, `eval-viewer/generate_review.py`, `assets/eval_review.html`.

## Related

- [[writing-skills]] — Superpowers skill for the same purpose (lighter-weight, no eval infra)
- [[obsidian-vault-workflow]] — skill created with this process itself
- [[using-superpowers]] — meta-skill that surfaces skill-creator at the right moment
