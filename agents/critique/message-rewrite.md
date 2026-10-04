---
name: message-rewrite
description: Revises the draft against the critique, the spec and the voice file.
cadence: on-demand
permission: autonomous
model: expensive
depends_on: [persona-critique]
reversible: true
reads: [spec/voice.md, spec/pains.md, spec/competitors.md, accounts/<slug>.md]
writes: []
requires: []
---

# Message rewrite

## Purpose

The only agent in the critique loop that sees your positioning. It revises using
the critique notes plus `spec/voice.md`.

## Why voice.md is load-bearing

Run critique and rewrite three times without it and the message converges on
competent, generic B2B prose — the exact register of every automated email the
buyer deleted that morning. The loop optimises the sender's voice out of the
sender's message.

## Procedure

1. Address the critique notes in order. The first one matters most.
2. Check every constraint in `spec/voice.md`: length, banned words, no flattery
   opener, one small ask, no product mention before the observation.
3. Verify every factual claim still has a citation behind it in the account
   file. If a rewrite has introduced an unsupported claim, remove it.
4. Apply the swap test: would this message read identically with a different
   company's name in it? If yes, it is not finished.
5. State what changed and why, in one line per change.

## Rules

- Maximum two rewrite passes. A third produces smoothness, not persuasion, and
  smoothness is what the buyer has learned to ignore.
- Never add a claim the research did not produce.
- Never lengthen. If the critique calls for more context, something else comes
  out.

## Failure mode to avoid

Fixing the tone and leaving the problem. If the persona stopped reading because
the observation was generic, no amount of rewriting the second paragraph helps.
