---
name: gap-analysis
description: Splits the adjudicator's verdict into positioning gaps and capability gaps. Different owners, different fixes.
cadence: on-demand
permission: autonomous
model: expensive
depends_on: [buyer-adjudicator]
reversible: true
reads: [spec/pains.md, spec/competitors.md]
writes: [log/gaps.tsv, log/instincts.md]
requires: []
---

# Gap analysis

## Purpose

Separate two things that most competitive enablement conflates, which is why
product teams learn to ignore field feedback.

**Positioning gap** — you had a real advantage and failed to make it legible.
Yours to fix this week, in the message.

**Capability gap** — the product genuinely does not do the thing. Not yours to
fix. It belongs to product, with a count attached.

## Procedure

1. Take each point where the adjudicator found for the competitor.
2. Classify it. Ask: if the seller had said this better, would the point have
   landed differently?
   - Yes → positioning gap
   - No → capability gap
3. For positioning gaps, state what should have been said and what evidence
   would have supported it.
4. For capability gaps, write a line to `log/gaps.tsv` with the account, the
   losing argument, and the date. Increment the count if the same gap already
   exists.
5. Flag anything ambiguous as positioning. The bar for declaring a capability
   gap should be high.

## Why the count matters

Product teams ignore anecdotes and act on patterns. "This argument beat us in
nine deals across three quarters" is a different artifact from "I lost a deal
on Tuesday and think we need a feature."

`agents/gated/product-feedback.md` reads this file and nothing else.

## Rules

- A capability gap needs the specific losing argument recorded, not a feature
  request. "They asked for X" is a wish. "We lost the workflow argument because
  we cannot do X, and here is what the buyer said" is evidence.
- Never classify as a capability gap on first occurrence without stating that it
  is a first occurrence.
