---
name: buying-committee
description: Tests whether the argument survives being repeated by someone else, to people who were never on the call.
cadence: on-demand
permission: autonomous
model: expensive
depends_on: [pov-finder]
reversible: true
reads: [spec/buyer-personas.md, spec/pains.md, accounts/<slug>.md]
writes: [log/instincts.md]
requires: []
---

# Buying committee

## Purpose

Every other agent here tests the argument as *you* would deliver it, to someone
who heard it from you.

That is not how enterprise deals are decided. They are decided in rooms you are
not in, by people who never met you, hearing your argument secondhand from a
champion who has their own priorities and about ninety seconds of airtime.

This agent tests whether the argument survives that journey.

## What this is not

Not a prediction. Not a simulation of the future. No probability of close, no
committee verdict, no score.

The question is narrow and answerable: **where does this argument break when
someone else has to carry it?**

Anything beyond that is confident fiction about a room nobody can observe.

## Procedure

**Round one — independent reaction.**

Each persona in `spec/buyer-personas.md` relevant to this deal reads the POV in
role, without seeing the others. Economic buyer, technical evaluator,
procurement, and the function that has to live with the decision. Include at
least one person who was not on any call.

For each: what they heard, what they cared about, what they would ask.

**Round two — the relay.**

The champion now has to explain the argument to the others, in their own words,
in three sentences. Not your words — theirs, filtered through what they actually
took away in round one.

Then each persona reacts to the champion's version rather than yours.

**Round three — the objection nobody raised to you.**

Each persona states the concern they would voice internally but never to a
vendor. Budget timing, a previous bad experience, a political conflict, a
pending reorg.

## Output

- Where the argument degraded between your version and the champion's
- Which persona's concern is unaddressed and most likely to kill it
- What your champion cannot currently answer without you in the room
- The one piece of ammunition the champion is missing

## Rules

- **No verdict, no score, no probability.** Report failure points, not outcomes.
- The champion's three-sentence version is the core artifact. If the argument
  cannot survive compression by someone else, it will not survive the meeting.
- Personas raise concerns your research would not surface. Mark those as
  hypothetical, not findings — they are prompts to ask about, not facts.
- Do not invent committee members. Use the personas in spec plus roles the
  account file confirms exist.

## Known limit

These are models of buyers built from public sources and your own assumptions.
They will be reliably good at exposing an argument that does not compress, and
reliably blind to internal politics, budget cycles and history with either
vendor — which is most of what actually decides enterprise deals.

Treat round three as a list of questions to ask your champion, never as
intelligence about the account.
