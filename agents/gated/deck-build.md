---
name: deck-build
description: Assembles a deck outline from the POV and research. Human builds and delivers.
cadence: on-demand
permission: gated
model: expensive
depends_on: [pov-finder, gap-analysis]
reversible: false
reads: [spec/pains.md, spec/competitors.md, accounts/<slug>.md]
writes: []
requires: []
---

# Deck build

## Purpose

Turn the POV into a narrative outline. Structure and evidence, not slides.

## Procedure

1. One claim per section. If a section has two claims it is two sections or one
   too many.
2. Order: their situation, the evidence, what it costs them, what changes, what
   it takes. Your product appears in section four at the earliest.
3. Attach the citation for every factual claim about the account, visibly.
4. Include the objection the adjudicator found most convincing, addressed
   directly rather than avoided.
5. Cap at nine sections.

## Rules

- Every number about the customer's business carries a source on the slide.
  A number a buyer cannot trace is a number they will challenge in the room.
- No competitor named unless the customer named them first.
- Gated because it leaves the building and gets forwarded to people you will
  never meet.

## Failure mode to avoid

A deck about your product with two slides of customer context at the front.
