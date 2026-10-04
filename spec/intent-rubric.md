# Intent rubric

> Adjust the threshold once you have calibration data. Until then it is a guess,
> and it should be a conservative one.

Scored by `agents/scoring/intent-scorer.md`, which runs as a **separate pass and
never sees the draft** — only the evidence. An agent that writes and grades its
own work is not a test.

## The five checks

| # | Check | Points |
| --- | --- | --- |
| 1 | Pain appears in the company's own language, not your category name | 0–3 |
| 2 | Claim cites a specific source and location | 0–3 |
| 3 | Evidence is inside its freshness window (`spec/freshness.md`) | 0–2 |
| 4 | A named person is attached to the pain | 0–2 |
| 5 | No disqualifier present | 0 or −10 |

Maximum 10.

## Thresholds

| Tier | Behaviour |
| --- | --- |
| 1 | Human reviews regardless of score |
| 2 | Score ≥ 7 → agent drafts and queues. Below → human reads first |
| 3 | Agent proceeds |

## Scoring notes

**Check 1 is the one that matters.** "They need better customer experience" is
your language. "The queue keeps growing and we can't hire our way out" is
theirs. Only the second is evidence.

**Check 2 has no partial credit for plausibility.** A claim you cannot cite
scores zero, however true it feels. A rep repeating an uncited claim to a CFO
has a problem no amount of fluency fixes.

**Check 5 is a penalty, not a zero**, so that a strong signal on a
partially-disqualified account still surfaces for a human to look at. Hard
disqualifiers are handled in `spec/scoring-model.md` and zero the account
outright.

## Known weakness

This rubric measures evidence quality. It does not measure timing, and timing
kills more outreach than wording does. A perfect 10 on an account in a hiring
freeze is still a bad send. Nothing here catches that. You do.
