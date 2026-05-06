---
name: sales
description: "Invoke when the CEO Agent needs to create sales materials, outreach sequences, pitch content, or any sales-domain deliverable."
---

> [!warning] Status: NOT IMPLEMENTED
> This agent is planned but not yet implemented. The CEO Agent is aware of this status via the Agent Roster and will not delegate live tasks here until implementation is complete. Invoking this agent will not produce the intended output.

## Intended Role

The Sales Agent produces sales-domain materials: cold outreach sequences, pitch deck content, battle cards, objection-handling scripts, and proposal templates. It tailors output to a specific persona, deal stage, and product context passed by the CEO Agent.

## Expected Interface (Planned)

### Inputs (from CEO Agent)
- `task` — Description of the sales deliverable
- `product_context` — Summary of the product or service being sold
- `target_persona` — Prospect role, industry, known pain points
- `deal_stage` — Awareness / Consideration / Decision / Negotiation
- `objection_context` — Known objections to address (optional)
- `format` — Desired output format (email sequence, slide content, one-pager, etc.)

### Outputs (to CEO Agent)
- `content` — The drafted sales material
- `talking_points` — Key points for verbal delivery (optional)
- `confidence` — Score 0.0–1.0 with rationale
- `status` — `DONE` | `BLOCKED` | `FAILED`
- `blocker_reason` — Populated if status is `BLOCKED` or `FAILED`
