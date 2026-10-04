---
name: followup-sequencer
description: Decides who has gone cold and whether a follow-up is warranted. Does not write it.
cadence: weekly
permission: autonomous
model: cheap
reversible: true
reads: [spec/territory.md, spec/boundaries.md, accounts/<slug>.md, log/touches.tsv]
writes: [log/instincts.md]
requires: []
---

# Follow-up sequencer

## Purpose

Sequencing is safe. Sending is not. This agent decides *whether* and *when*;
`agents/gated/followup-draft.md` writes the thing, behind a gate.

Splitting them is the clearest illustration of this repo's architecture.

## Procedure

1. Read `log/touches.tsv` for this account. Count touches this quarter against
   the cap in `spec/boundaries.md`.
2. If at or over cap, stop. Report that the cap is reached. Do not recommend an
   exception.
3. Compute days since last meaningful contact — a reply, not a send.
4. Check whether anything has changed since the last touch. A follow-up with no
   new information is a reminder that you want something.
5. Recommend follow-up only where both are true: enough time has passed, and
   there is something new to say.

## Rules

- No new information, no follow-up. This is the whole rule.
- Three unanswered sends is the end of a sequence, not a prompt for a fourth.
- Never recommend a follow-up whose content would be "just checking in".

## Failure mode to avoid

Treating silence as a scheduling problem. Usually it is an answer.
