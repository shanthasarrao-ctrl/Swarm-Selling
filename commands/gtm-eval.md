---
name: gtm-eval
description: Runs the fixture set and diffs against expected findings. Did a spec change help?
---

# /gtm-eval

## Purpose

The only way to tell whether a change to `spec/` improved anything without
waiting a quarter for deals to close.

Ten frozen public companies in `evals/fixtures/`, with known findings in
`evals/expected/`.

## Procedure

1. Run the research stack against every fixture.
2. Diff the output against `evals/expected/`.
3. Report per fixture: findings hit, findings missed, findings invented.
4. Report the aggregate against the last run.

## What it measures

Whether the research stack still surfaces things you already know are there.
It catches regression — a spec edit that quietly breaks retrieval, a prompt
change that makes an agent miss what it used to find.

## What it does not measure

Whether you will close more deals. Nothing here can tell you that. The fixtures
are a smoke test, not a market.

## Rules

- Fixtures are frozen. If a company's filings change, the fixture does not.
- "Findings invented" is the most important number on the report. An agent that
  hits every expected finding and adds three fabricated ones is worse than one
  that misses two.
