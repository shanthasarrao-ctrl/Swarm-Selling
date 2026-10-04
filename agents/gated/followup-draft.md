---
name: followup-draft
description: Writes a follow-up, but only when the sequencer has found something new to say.
cadence: on-demand
permission: gated
model: expensive
depends_on: [followup-sequencer]
reversible: false
reads: [spec/voice.md, spec/boundaries.md, accounts/<slug>.md, log/touches.tsv]
writes: [log/touches.tsv]
requires: []
---

# Follow-up draft

## Precondition

`agents/autonomous/followup-sequencer.md` must have recommended a follow-up.
That agent only recommends one when two things are true: enough time has passed,
and something new exists to say.

If the sequencer did not recommend one, this agent does not run. There is no
override.

## Procedure

1. Lead with the new information. That is the entire reason for the message.
2. Reference the prior thread in at most one clause.
3. Make the ask smaller than last time, not the same size.
4. Apply `spec/voice.md`.

## Rules

- Never write "just checking in", "circling back", "bumping this", or any
  variant. If that is all you have, the sequencer was wrong and you should stop.
- Three unanswered sends ends the sequence. There is no fourth.
- Silence is usually an answer, not a scheduling problem.

## Failure mode to avoid

A follow-up whose only content is that you would like a reply.
