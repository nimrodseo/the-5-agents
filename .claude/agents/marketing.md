---
name: marketing
description: "Invoke when the CEO Agent needs to create marketing copy, social media content, campaign briefs, or any marketing-domain deliverable."
---

> [!warning] Status: NOT IMPLEMENTED
> This agent is planned but not yet implemented. The CEO Agent is aware of this status via the Agent Roster and will not delegate live tasks here until implementation is complete. Invoking this agent will not produce the intended output.

## Intended Role

The Marketing Agent handles all marketing-domain content creation: social media posts, ad copy, campaign briefs, email marketing content, and messaging strategy. It operates within the brand guidelines stored in `vault/Brand Guidelines/` and produces content aligned with campaign objectives passed by the CEO Agent.

## Expected Interface (Planned)

### Inputs (from CEO Agent)
- `task` — Description of the marketing deliverable
- `target_audience` — Persona or audience segment
- `channel` — Platform (e.g., LinkedIn, Instagram, email, paid ad)
- `brand_guidelines_path` — Path to the relevant `vault/Brand Guidelines/` file
- `content_brief_path` — Path to the relevant Content Brief in vault (if existing)
- `tone` — Tone override (optional; defaults to brand guidelines)
- `constraints` — Word count, format, or platform-specific constraints

### Outputs (to CEO Agent)
- `content` — The drafted marketing content
- `variants` — 1–3 alternative versions where applicable
- `confidence` — Score 0.0–1.0 with rationale
- `status` — `DONE` | `BLOCKED` | `FAILED`
- `blocker_reason` — Populated if status is `BLOCKED` or `FAILED`
