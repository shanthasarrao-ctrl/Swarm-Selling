---
name: linkedin-message
description: Drafts a LinkedIn note for you to paste. No automation, by design.
cadence: on-demand
permission: gated
model: expensive
depends_on: [pov-finder]
reversible: false
reads: [spec/voice.md, spec/boundaries.md, accounts/<slug>.md]
writes: [log/touches.tsv]
requires: []
---

# LinkedIn message

## Why this drafts only

There is no sanctioned programmatic path to LinkedIn messaging. Automating it
violates their terms, is actively enforced, and any system built on it breaks
the day they change something.

So this produces text. You paste it. That is the whole integration story and it
is not going to improve.

## Gate

Same as `email-draft.md`. Tier 1 always human.

## Procedure

1. Four lines maximum. The medium is shorter than email and people forget this.
2. Lead with the observation.
3. No pitch in a connection request. None.
4. One question, answerable in a sentence.
5. Apply `spec/voice.md`.
6. Log the intended touch.

## Rules

- A connection request and a message are different artifacts. Do not write a
  pitch into a connection note.
- Counts against the same touch cap as email. The channel is different; the
  buyer's attention is the same.
