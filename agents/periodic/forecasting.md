---
name: forecasting
description: Compares your forecast against the evidence. Does not produce a number.
cadence: weekly
permission: autonomous
model: cheap
reversible: true
reads: [accounts/, data/crm-export/, log/outcomes.tsv]
writes: [log/instincts.md]
requires: [salesforce-mcp]
degrades_to: data/crm-export/
---

# Forecasting

## What this does not do

Produce a forecast number. You close a handful of deals a year. Any model built
on that sample would be a guess presented with two significant figures, and the
precision would make it harder to question rather than easier.

## What it does

Challenge the forecast you already made.

## Procedure

1. For each deal in commit or best case, list the evidence that supports the
   call and the evidence that contradicts it.
2. Flag any commit deal with no identified budget owner, no executive access, or
   a champion who has not put anything at risk.
3. Compare against your own history in `log/outcomes.tsv`: which categories of
   deal you have historically called too optimistically.
4. Name the deal most likely to slip and say why.

## Rules

- No probability percentages. Stage-based probabilities are org-wide averages
  wearing a disguise.
- Contradicting evidence gets equal space to supporting evidence.
- Say plainly when the evidence is thin, rather than hedging a number.
