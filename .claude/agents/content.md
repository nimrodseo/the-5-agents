---
name: content
description: "Invoke when the CEO Agent needs to create long-form or general content — blog posts, articles, documentation, reports, or any non-marketing, non-sales written deliverable."
---

> [!warning] Status: NOT IMPLEMENTED
> This agent is planned but not yet implemented. The CEO Agent is aware of this status via the Agent Roster and will not delegate live tasks here until implementation is complete. Invoking this agent will not produce the intended output.

## Intended Role

The Content Agent handles general-purpose long-form content creation: blog posts, thought-leadership articles, documentation, internal reports, and structured narratives. It differs from the Marketing Agent in scope — Content produces depth-focused pieces rather than campaign-specific copy — and from the Sales Agent in purpose — Content does not have conversion as a primary objective.

## Expected Interface (Planned)

### Inputs (from CEO Agent)
- `task` — Description of the content deliverable
- `topic` — Main subject and angle
- `format` — Blog post / article / documentation / report / other
- `target_audience` — Intended reader
- `target_length` — Word count or length range
- `tone` — Formal / conversational / technical / narrative
- `content_brief_path` — Path to brief in vault (if existing)
- `sources` — Reference materials or existing content to draw from (optional)

### Outputs (to CEO Agent)
- `content` — The drafted piece
- `metadata` — Suggested title, meta description, tags
- `confidence` — Score 0.0–1.0 with rationale
- `status` — `DONE` | `BLOCKED` | `FAILED`
- `blocker_reason` — Populated if status is `BLOCKED` or `FAILED`
