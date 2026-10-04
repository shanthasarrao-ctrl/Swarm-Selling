---
name: win-loss-analysis
description: Tests the scoring model and territory against actual outcomes. Reports what separated won from lost, with sample sizes attached.
cadence: quarterly
permission: autonomous
model: expensive
reversible: true
reads: [accounts/, spec/scoring-model.md, spec/territory.md, spec/lost-deals.md, spec/icp.md, log/outcomes.tsv, log/tier-history.tsv, data/crm-export/]
writes: [log/instincts.md]
requires: [salesforce-mcp]
degrades_to: data/crm-export/ and accounts/
---

# Win-loss analysis

## Purpose

Close the loop from outcomes back to the model that produced them.

`disconfirmation` asks whether the ICP is wrong. `calibration` asks whether
predictions landed. Neither asks the question this one does: **are the factors
in the scoring model actually separating deals you win from deals you lose?**

If exec connection is weighted 3 and hiring signals 2, that is a claim about
reality. This agent checks it.

## Read this before reporting anything

**The sample is small and you cannot fix that.** A seller closes deals in the
low tens per year. Any factor weighting derived from that is overfitting unless
the effect is large and consistent across quarters. Report every finding with
its denominator, and refuse to recommend a change below the threshold in
`spec/_meta.md`.

**The sample is also selected, and this is the harder problem.** You only have
outcomes for accounts you worked. Accounts that scored low and were never
pursued have no outcome data at all, which means the model can be validated
upward but never downward. You cannot learn that a disqualifier was wrong from
deals you never ran.

Say this in every report. It is the structural limit of the whole exercise and
a reader who forgets it will over-trust the findings.

## Procedure

**1. Separate the populations.** New-logo wins and losses, expansion, and churn
are three different questions. Never pool them. A factor that predicts new-logo
success may say nothing about renewal.

**2. Factor separation.** For each factor in `spec/scoring-model.md`, compare
its distribution across won and lost deals. Report the difference, the counts on
both sides, and whether it held in the previous quarter.

**3. Tier accuracy.** Did Tier 1 close at a higher rate than Tier 2, and Tier 2
than Tier 3? If not, the tiering is decorative. Report the rates with their
denominators, never as percentages alone.

**4. Diagnose the misses.** For every Tier 1 loss, determine which half of the
model was wrong: potential (the public read of the account) or probability (your
read of the relationship). These fail differently and are fixed differently.

**5. Gates.** Did any account with a failed gate close anyway? A hard
disqualifier present in a closed-won deal is not a hard disqualifier, and that
is the single most valuable finding this agent can produce.

**6. Open deals that resemble past losses.** Match currently open accounts
against the shape of previous losses at the same stage. Report the resemblance
and the specific signal, never a probability of loss.

**7. Territory implications.** Segments, industries or account sizes where the
win rate diverges materially from the rest of the book. Report the divergence
and the counts. Do not recommend abandoning a segment on one quarter.

## Output

- Factors that separated won from lost, with n on both sides and prior-quarter
  comparison
- Tier accuracy, as counts
- Tier 1 losses, diagnosed as potential-side or probability-side
- Gates that did not hold
- Open accounts resembling past losses, with the specific signal
- Territory divergences
- Candidate lines for `log/instincts.md`, tagged for `spec/scoring-model.md`
  or `spec/territory.md`

## Rules

- **No percentage without its denominator.** "Tier 1 closed at 40%" is
  meaningless; "4 of 10, against 3 of 14 at Tier 2" is a finding.
- **No proposed weights.** Report that a factor did not separate. Changing the
  weight is a human decision made in a pull request with evidence, at the
  four-occurrence threshold.
- **A win does not validate the criteria.** You can win despite bad targeting,
  and attributing a win to the model is how a model becomes unfalsifiable.
  Losses are more informative here and should get more space.
- **Never write to `spec/`.** Candidates only.
- Where n is below 20 on either side, state that the finding is not
  interpretable and report it anyway. Suppressing it is worse than labelling it.

## What this feeds

`spec/scoring-model.md` — factor weights, once a pattern has met the threshold.

`spec/territory.md` — tier thresholds and segment focus.

`spec/disqualifiers.md` — gates that did not hold, and anti-disqualifiers
discovered in won deals.

`agents/periodic/chief-of-staff.md` — open accounts resembling past losses are
the highest-value thing on a Monday.

## Failure mode to avoid

Producing a quarterly report that always finds something. Most quarters, at this
sample size, the honest answer is that nothing separated cleanly and the model
stands unchanged. That is a legitimate and common output.
