---
name: deal-desk
description: Assembles a finance or deal-desk approval package. Does not decide, does not submit.
cadence: on-demand
permission: internal
model: expensive
reversible: false
reads: [accounts/<slug>.md, spec/competitors.md, spec/lost-deals.md, data/crm-export/]
writes: [log/internal-requests.tsv]
requires: [salesforce-mcp]
degrades_to: data/crm-export/
---

# Deal desk

## Purpose

Assemble the package a deal desk actually needs, so the approval takes one pass
instead of three.

Most discount requests get bounced not because the ask is wrong but because the
justification is missing. That round trip costs days at the exact point in a
cycle where days matter.

## What it produces

1. **The ask.** Specific terms: discount percentage, payment terms, contract
   length, anything non-standard.
2. **Why now.** The timing pressure, and whether it is the customer's or yours.
   Say which honestly — deal desks can tell.
3. **Precedent.** Comparable approved deals, from your own history. Shape and
   size, not customer names if this repo is shared.
4. **What it buys.** What the customer commits to in return. An unreciprocated
   discount is a price cut.
5. **The alternative.** What happens if this is declined — realistically, not as
   leverage. "We lose the deal" is a claim a deal desk will check.
6. **Competitive context.** Who else is in it and what is publicly knowable
   about their pricing posture. Never a competitor's actual quote.

## Rules

- **Does not decide.** Whether a discount is justified is a commercial judgment
  belonging to someone with a different set of incentives than yours.
- **Does not submit.** It assembles. A human sends.
- No invented ROI. If you have not built a business case with the customer, say
  the business case is not yet built.
- Never state that a deal is lost without the discount unless the customer said
  so, and quote them if they did.

## The cap

Internal requests count against the limit in `spec/boundaries.md`. Deal desk
attention is a shared resource and the people who use it carelessly get queued
behind the people who do not.

## Failure mode to avoid

Making it frictionless to ask for a discount. Friction is doing useful work
here.
