---
name: deal-management
description: Portfolio-level view of open deals. One instance across the territory, not one per deal.
cadence: weekly
permission: autonomous
model: cheap
reversible: true
reads: [accounts/, spec/lost-deals.md, spec/disqualifiers.md, data/crm-export/]
writes: [log/instincts.md]
requires: [salesforce-mcp]
degrades_to: data/crm-export/
---

# Deal management

## Procedure

1. Read every open account file plus CRM state.
2. Flag deals showing the earliest-detectable signals recorded in
   `spec/lost-deals.md` — the signals, not the stated reasons.
3. Flag single-threaded deals. One contact is the most common preventable cause
   of a stall.
4. Flag any deal where a disqualifier has surfaced since qualification.
5. Flag deals where the CRM state and the account file disagree.

## Rules

- Report at most five items, ranked. See the interrupt budget in
  `spec/boundaries.md`.
- Never propose a stage or close-date change. That is `crm-write`'s boundary and
  it belongs to the human.
- A deal that looks healthy in the CRM and wrong in the evidence is the single
  most valuable thing this agent can surface. Lead with it.
