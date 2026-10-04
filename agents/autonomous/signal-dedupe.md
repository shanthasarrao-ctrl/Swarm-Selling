---
name: signal-dedupe
description: Suppresses signals already surfaced. Runs last, before anything reaches a human.
cadence: weekly
permission: autonomous
model: cheap
reversible: true
reads: [log/seen-signals.tsv, spec/boundaries.md]
writes: [log/seen-signals.tsv]
requires: []
---

# Signal dedupe

## Purpose

A weekly scheduled run will surface the same risk factor every Monday for a
year unless something stops it. This is the thing that stops it.

Alert fatigue is the failure mode that kills these systems in practice. They do
not break — people just stop reading them.

## Procedure

1. Hash each candidate signal on account, source type and substance. Substance,
   not wording — a rephrased version of the same finding is the same finding.
2. Suppress anything already in `log/seen-signals.tsv`.
3. Let a suppressed signal through only if it has materially changed: the risk
   moved up the ordering, the language intensified, a number changed.
4. Record what was surfaced and when.
5. Enforce the interrupt budget in `spec/boundaries.md`. Five items per week
   across the whole territory. If more survive, rank and cut.

## Rules

- When in doubt, suppress. A missed signal costs one week. A noisy feed costs
  the user's attention permanently.
- Never re-surface a signal a human has explicitly dismissed.
- Most weeks, most accounts should produce nothing. That is correct output.
