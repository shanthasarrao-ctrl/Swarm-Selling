---
name: calibration
description: Scores predictions against outcomes. The closest this system gets to a test.
cadence: quarterly
permission: autonomous
model: cheap
reversible: true
reads: [log/predictions.tsv, log/outcomes.tsv, log/tier-history.tsv]
writes: [log/instincts.md]
requires: []
---

# Calibration

## Purpose

Ask whether any of this works.

## What gets checked

1. **Tiering.** Did Tier 1 accounts close at a higher rate than Tier 2? If not,
   the scoring model is decorative.
2. **The orchestrator.** When it said an account mattered this week, did
   anything follow?
3. **The adjudicator.** Did cases it found unconvincing lose more often?
4. **The intent rubric.** Did high-scoring signals produce more replies?

## Procedure

1. Join predictions to outcomes on account and date.
2. Report base rates alongside every result. A 30% reply rate means nothing
   without the overall rate beside it.
3. State the sample size before the finding, every time.
4. Where n < 20, say the result is not interpretable and report it anyway.

## The honest limit

This is not Karpathy's ratchet and it never will be. A cheap objective scorer
returns a verdict in minutes on thousands of trials. You close a handful of
deals a year, each confounded by territory, timing and someone's mood.

Calibration here takes quarters and may never be conclusive. Its real value is
catching the case where the system is clearly, badly wrong — not fine-tuning a
system that is roughly right.

## Rules

- Never report a percentage without its denominator.
- Never recommend a spec change from this data alone. Feed it to
  `disconfirmation` and let the four-occurrence rule apply.
