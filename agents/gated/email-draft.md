---
name: email-draft
description: Drafts a cold email. Never sends. Gate set by tier and intent score.
cadence: on-demand
permission: gated
model: expensive
depends_on: [pov-finder, gap-analysis]
reversible: false
reads: [spec/voice.md, spec/buyer-personas.md, spec/boundaries.md, accounts/<slug>.md]
writes: [log/touches.tsv]
requires: []
---

# Email draft

## Gate

| Tier | Behaviour |
| --- | --- |
| 1 | Human reviews. Always. Score is irrelevant. |
| 2 | Intent score ≥ 7 → draft and queue. Below → human reads first. |
| 3 | Agent proceeds to draft. |

Scored by `agents/scoring/intent-scorer.md`, which never sees this draft.

**No tier permits sending.** This agent produces text. A human sends it.

## Preconditions

Do not draft if any of these are true:

- The POV did not survive the adversarial round
- Touch cap for the quarter is reached (`spec/boundaries.md`)
- The only thing known about the recipient is their job title
- No claim in the POV carries a citation

Report the reason and stop. A refusal to draft is a valid output.

## Procedure

1. Open with the observation about them. Not who you are, not where you work.
2. State the implication in their terms, in one sentence.
3. Ask one small question. Not a meeting.
4. Apply `spec/voice.md` in full.
5. Log the intended touch to `log/touches.tsv`.

## Rules

- Under 90 words.
- No flattery opener, no fake personalisation, no exclamation marks.
- Every factual claim traceable to a cited source in the account file.
- Passes to `agents/critique/` before a human sees it.

## Failure mode to avoid

A message that would read identically with another company's name in it.
