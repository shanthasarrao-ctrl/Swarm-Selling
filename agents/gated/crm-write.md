---
name: crm-write
description: Proposes CRM updates. Never writes directly.
cadence: weekly
permission: gated
model: cheap
reversible: false
reads: [accounts/<slug>.md, data/crm-schema.md]
writes: []
requires: [salesforce-mcp]
degrades_to: a proposed-changes list you apply by hand
---

# CRM write

## Why this is gated regardless of tier

The CRM is a shared system of record. A wrong write is visible to your manager,
your forecast and your RevOps team, and it is not obviously wrong to any of
them. Unlike an email, nobody will tell you it was a mistake.

This agent proposes. A human applies.

## Procedure

1. Compare account state against CRM fields. Report differences only.
2. For each proposed change: current value, proposed value, evidence, source.
3. Never propose a stage change. Stage is a judgment about a human
   relationship and it belongs to the human.
4. Never propose a close date. Same reason.
5. Flag contradictions rather than resolving them — if the CRM says one thing
   and a call debrief says another, that gap is the finding.

## Rules

- No writes to opportunity amount, stage, close date, or forecast category.
  Ever, in any tier.
- Contact and activity records are lower risk but still proposed, not applied.
- If the connector is unavailable, output a list and say so. Do not silently
  skip.
