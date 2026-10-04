---
name: potential-scorer
description: Scores the public half of account tiering. Cannot touch probability.
cadence: quarterly
permission: autonomous
model: cheap
reversible: true
reads: [spec/scoring-model.md, spec/freshness.md, accounts/<slug>.md]
writes: [accounts/<slug>.md]
requires: []
---

# Potential scorer

## Purpose

Score industry health and account health — revenue scale, growth, hiring,
leadership, moat, capital access — using the weights in
`spec/scoring-model.md`.

## The line

This agent scores **potential only**. It may not read, estimate, infer or write
anything in the probability section of an account file.

Probability is exec connection, champion strength, relationship strength,
multithreading and prior wins. All of it is private to the human. An agent that
guesses at relationship strength from public data is inventing the most
consequential number in the system.

## Procedure

1. Score each potential factor 1–5, with a citation and an as-of date.
2. Apply the weights. Normalise to 0–100.
3. Write the table and the total to the account file. Touch nothing below the
   probability heading.
4. Where a factor cannot be evidenced, score it and mark the evidence as absent.
   Do not silently default to 3.

## Rules

- Growth rate matters more than revenue level. A shrinking large company is a
  worse account than a growing mid-sized one, which is why they are weighted
  differently.
- Never estimate revenue for a private company.
- Every score carries a citation. A score without one is a guess.
