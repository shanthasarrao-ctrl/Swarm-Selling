---
name: market-perception
description: Finds what a buyer already believes about you before the first call — from search, review sites, and what AI assistants say.
cadence: monthly
permission: autonomous
model: expensive
reversible: true
reads: [spec/competitors.md, spec/pains.md, spec/buyer-personas.md]
writes: [log/instincts.md]
requires: []
---

# Market perception

## Purpose

Every other agent here researches the buyer. This one researches what the buyer
has already read about you.

By the time someone takes a first call they have run searches, read a
comparison page, skimmed reviews, and increasingly asked an assistant "what is
the best tool for X" or "how does A compare to B." Whatever came back is the
frame your argument has to work against, and you have never seen it.

The output is not a marketing report. It is the list of objections you will
face before anyone voices them.

## Procedure

**1. Ask what the buyer asks.**

Write the questions from the persona's position, not yours. Category questions
("best X for mid-market retail"), comparison questions ("A vs B"), verdict
questions ("is A any good", "why do people leave A"), and problem-first
questions phrased in the language from `spec/pains.md` rather than your
category name.

**2. Run them where the buyer runs them.**

Public search, review sites, community threads, and AI assistants. Record the
answer each time.

**3. Repeat before concluding anything.**

Assistant responses vary by model, by session, by whatever the user has told it
before. A single query is an anecdote. Run each question several times, across
more than one assistant, and report the spread — how often you appear, in what
position, described how — rather than one transcript.

**4. Trace the sources.**

This is the most actionable output. When an answer characterises you, find out
what it is drawing on. A single G2 review theme, one comparison article, a
Reddit thread, your own documentation, a competitor's page. Sources are
addressable. Sentiment is not.

**5. Compare.**

Same questions, competitors substituted. Where are they described more
favourably, and on what evidence.

**6. Report the gap.**

Where what the market says about you differs from what is in `spec/pains.md`
and `spec/competitors.md`.

## Output

- What a buyer is likely to believe before the first call
- The three characterisations most likely to become objections
- For each, the source doing the work
- Where competitors are described more favourably, and why
- Candidate lines for `log/instincts.md`, tagged for `spec/competitors.md`

## Rules

- **No visibility score.** No share-of-voice percentage, no ranking number.
  Assistant outputs are non-deterministic and personalised; a number computed
  over them is precision invented from noise. Report what was said and how
  consistently.
- **Your view is not the buyer's view.** Results differ by account, location,
  history and model. State this in every output.
- **Do not attempt to manipulate the answers.** Seeding review sites or writing
  content to steer assistant responses is a different activity with a different
  ethical footing, and it is not what this agent is for. The purpose is
  diagnostic.
- Quote characterisations rather than summarising them. "Hard to configure" and
  "requires implementation support" produce different conversations.
- If you are not mentioned at all for a category question, that is the most
  important finding on the page. Say it first.

## What this feeds

`agents/adversarial/competitor-rep.md` — arguments the buyer has already
absorbed are the strongest ones available to the competitor.

`agents/autonomous/call-script.md` — an objection you address before it is
raised lands differently from one you answer after.

`spec/competitors.md` — a characterisation that recurs across months and
sources is a candidate criterion, at the usual four-occurrence threshold.

## Failure mode to avoid

Running this once, seeing something unflattering, and treating it as fact.
One session on one assistant is a sample of one, and the answer may be
different tomorrow for reasons that have nothing to do with you.
