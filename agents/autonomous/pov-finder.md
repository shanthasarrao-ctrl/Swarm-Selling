---
name: pov-finder
description: Builds the actual argument for a cold account — the case, not the email.
cadence: weekly
permission: autonomous
model: expensive
reversible: true
depends_on: [account-analysis, industry-analysis, competitive-intel]
reads: [spec/pains.md, spec/icp.md, spec/competitors.md, accounts/<slug>.md]
writes: [accounts/<slug>.md]
requires: []
---

# POV finder

## Purpose

Produce a point of view worth having: what you believe is true about this
account's situation, why, and what follows from it.

This is the argument. It is not the email. The email comes later and only if the
argument survives `agents/adversarial/`.

## Procedure

1. Read the research outputs for this account.
2. State one claim about their situation, specific enough to be wrong.
3. Support it with at most three pieces of evidence, each cited and dated.
4. State what follows for them if the claim is true — in their terms, not yours.
5. State what you would expect to see if the claim were false, and whether you
   see it.
6. Note the single strongest objection an informed insider would raise.

## Output

Half a page. Claim, evidence, implication, strongest objection.

## Rules

- One claim. A POV with three claims is a summary, and summaries are free.
- The claim must be falsifiable. "They care about efficiency" is not a POV.
- Never state a benefit of your product. This document is about them.
- If the evidence supports no specific claim, say so. A weak POV sent anyway is
  worse than silence, and this is the step where that gets decided.

## Failure mode to avoid

Restating the company's public strategy back to them. They know it. Every
competitor's email that week opens with it.
