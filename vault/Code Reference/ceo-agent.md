---
title: CEO Agent
file: .claude/agents/ceo.md
type: agent-definition
status: active
created: 2026-05-06
---

## Overview

The CEO Agent is the sole orchestration layer of the 5-agents content creation system. It is defined as a Claude Code sub-agent in `.claude/agents/ceo.md` and is dispatched via the Task tool. It does not produce content directly — it directs, coordinates, and verifies the agents that do.

**Architecture decision:** `ceo.md` is a sub-agent definition (invoked via Task dispatch), not a behavior modifier for main Claude. `CLAUDE.md` describes the agent hierarchy and how to invoke the CEO — the rules live exclusively inside `ceo.md`.

---

## File Location

`.claude/agents/ceo.md`

---

## Agent Identity

- **Name (frontmatter):** `ceo`
- **Role:** Orchestration and decision-making
- **Status:** Active (fully implemented)
- **Tone:** Sharp, operational, no padding, no fake certainty

---

## Key Sections

### Standard Workflow (9 steps)
1. Receive — accept user request in full
2. Analyze — decompose into subtasks, identify agents and order
3. Plan — build action plan with sequence, dependencies, expected outputs
4. Check approval gates — review every step against Human Approval Gates list
5. Request approval — present full plan, wait for explicit confirmation
6. Activate agents — dispatch with full context per Delegation Protocol
7. Monitor — track status; handle BLOCKED and FAILED
8. Verify — check outputs meet requirements; flag inconsistencies
9. Consolidate and return — merge outputs, write session log, return to user

### Human Approval Gates
Mandatory stop-and-ask before: modifying files on disk, publishing/deploying, sending messages/emails, external API writes, database operations, deleting resources, any irreversible action.

### Agent Roster
| Agent | Status |
|---|---|
| CEO | Active |
| Marketing | Not Implemented |
| Sales | Not Implemented |
| Dev | Not Implemented |
| Content | Not Implemented |

### Delegation Protocol
Task prompt must include: agent name + file path, full task description, expected output format, hard constraints and dependencies.

### Orchestration Patterns
- **Sequential:** when each step depends on the previous output
- **Parallel:** when agents are independent and share no state
- **Conflict resolution:** compare reasoning + confidence, present both to user, request decision

### Failure Handling
- Transient failure → retry once with identical inputs
- Repeated failure → escalate to user (reason + options)
- Unstable state (multiple failures/conflicts) → stop all execution immediately

### Output Format
Every CEO response: `[STATUS: <queue state>]` + what happened + what's next + approval requests clearly marked.

---

## Sub-Agent Stubs

The 4 planned sub-agents each have a stub file under `.claude/agents/`:

| Agent | File | Interface Status |
|---|---|---|
| Marketing | `.claude/agents/marketing.md` | Inputs/Outputs defined, not implemented |
| Sales | `.claude/agents/sales.md` | Inputs/Outputs defined, not implemented |
| Dev | `.claude/agents/dev.md` | Inputs/Outputs defined, not implemented |
| Content | `.claude/agents/content.md` | Inputs/Outputs defined, not implemented |

---

## Related

[[vault-initial-setup]] | [[skill-creator-installation]] | [[obsidian-vault-workflow]]

---

## Session Log

### 2026-05-06 — CEO Agent definition [completed]
Created all 5 agent files (ceo.md + 4 stubs) per 3-batch implementation plan. CEO Agent is fully defined and active. Sub-agents are stubbed with planned interfaces, marked NOT IMPLEMENTED.
