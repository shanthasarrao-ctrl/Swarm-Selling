---
name: call-script
description: Preparation for a live call. Looks like outreach, is actually a script you perform.
cadence: on-demand
permission: autonomous
model: expensive
depends_on: [pov-finder]
reversible: true
reads: [spec/pains.md, spec/competitors.md, spec/voice.md, accounts/<slug>.md]
writes: []
requires: []
---

# Call script

## Why this is autonomous

Nothing sends. You read it, then you speak. The human is the interface, which
makes this preparation rather than outreach.

## Procedure

1. Open with the observation from the POV, in one sentence, in their language.
2. Write the question that follows from it — open, specific, answerable in
   thirty seconds.
3. List the three objections most likely on this account, drawn from
   `spec/lost-deals.md` and `spec/competitors.md`, with a response to each that
   is a question rather than a rebuttal.
4. Write the disqualifying question — the one whose answer would tell you to
   walk away. Put it in the first five minutes, not the last.
5. Note what you are trying to learn, as distinct from what you are trying to
   say.

## Rules

- Under 200 words. A script you have to read is a script you will read aloud.
- No product mention in the first two minutes.
- The disqualifying question is mandatory. A script without one is a pitch.

## Failure mode to avoid

Writing a monologue. The output should be four prompts and a list, not prose
you deliver.
