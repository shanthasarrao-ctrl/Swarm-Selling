---
name: criteria-maintenance
description: Reports which parts of the spec have expired or lost their evidence. Fixes nothing.
cadence: monthly
permission: autonomous
model: cheap
reversible: true
reads: [spec/]
writes: []
requires: []
---

# Criteria maintenance

## Why this exists

Stale config breaks a build loudly. A stale ICP routes the wrong accounts
quietly for three quarters while you blame the market.

There is no error signal in sales. The dating and expiry mechanism is the only
alarm available, and this agent is the thing that rings it.

## Procedure

1. Read every `set:` date in `spec/`.
2. Apply the expiry table in `spec/_meta.md` — strong 12 months, moderate 6,
   weak 3.
3. Report what has expired, grouped by file, oldest first.
4. Report criteria carrying no `evidence:` field. Those are opinions and should
   be labelled as such.
5. Report contradictions — a criterion in one file that conflicts with another,
   usually because someone edited one and not the other.
6. Report placeholder text still present from the shipped templates.

## Rules

- **Fix nothing.** Re-confirming a criterion requires knowing whether the market
  moved, which this agent cannot know. Expiry is a prompt for a human.
- Do not propose replacement values.
- Report even when nothing has expired. A clean run is information.
