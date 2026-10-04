---
name: gtm-brief
description: Runs the research and adversarial stack for one account.
---

# /gtm-brief <account-slug>

## Preflight

1. Run `/gtm-check`. If it reports BLOCKING placeholder content, stop.
2. Confirm the account has an identity block and a tier.

## Run

Execute `swarm/deal-swarm.yaml` for an open opportunity, or
`swarm/prospect-swarm.yaml` for a cold account.

Stop after wave 4 by default. The output is the case and the adjudication —
not a message. Drafting is a separate, deliberate act.

## Output

One page:

- Thesis: fits / partially fits / does not fit
- Evidence for, cited and dated
- Evidence against, cited and dated
- What the competitor rep argued, and how the adjudicator found
- Positioning gaps — yours to fix
- Capability gaps — logged, not yours
- What changed since the last run

## Rules

- Every claim carries a citation and an as-of date.
- If nothing has changed since the last run, say that and stop. It is the most
  common correct output.
