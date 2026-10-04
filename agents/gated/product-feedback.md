---
name: product-feedback
description: Turns accumulated capability gaps into a pattern report for product. Reads log/gaps.tsv and nothing else.
cadence: monthly
permission: gated
model: expensive
depends_on: [gap-analysis]
reversible: false
reads: [log/gaps.tsv]
writes: []
requires: []
---

# Product feedback

## Purpose

Product teams ignore anecdotes and act on patterns. This exists to make sure
what reaches them is the second kind.

## Threshold

A gap is reported when it has appeared **four or more times** across distinct
accounts. Below that it stays in `log/gaps.tsv` and accumulates.

One lost deal is not evidence. It is a story, usually with more than one
explanation, and sending it to product spends credibility you will want later.

## Procedure

1. Read `log/gaps.tsv`. Group by losing argument, not by requested feature.
2. For each group at or above threshold: the argument that beat you, the number
   of occurrences, the accounts, the date range, and what the buyer actually
   said in each.
3. State the revenue exposure honestly — deal sizes involved, without
   extrapolating to a market opportunity.
4. Separate what you know from what you are inferring.

## Rules

- Report the losing argument, never a feature request. "They asked for X" is a
  wish; "we lost the workflow argument four times because we cannot do X, here
  is what each buyer said" is evidence.
- Do not include positioning gaps. Those are yours. `gap-analysis` already
  separated them.
- Do not estimate market size. You are reporting from your own pipeline.

## Failure mode to avoid

Being the rep who forwards every lost deal to product. It works once.
