---
name: gtm-tier
description: Scores one account. Agent does potential, you do probability.
---

# /gtm-tier <account-slug>

## Procedure

1. Run `identity-resolver` if the identity block is incomplete.
2. Run `potential-scorer`. It fills the public half: industry health, revenue,
   growth, hiring, leadership, moat, capital access. Every score cited and
   dated.
3. Show the seller the potential table and the total.
4. **Then interview them for probability.** One factor at a time, from
   `spec/scoring-model.md`:
   - Exec connection
   - Champion strength — this is a gate, not a score
   - Relationship strength
   - Multithreading
   - Prior wins in similar accounts
   - Category need
   - Prior category purchase
5. Apply gates. A failed gate zeroes the axis rather than deducting from it.
6. Compute `(potential/100) × (probability/100) × 100`, assign the tier from
   `spec/territory.md`, write to the account file, append to
   `log/tier-history.tsv`.

## Rules

- Never estimate a probability factor. If the seller does not know whether they
  have executive access, the answer is that they do not.
- Never write below the probability heading without their answers.
- Show the arithmetic. A tier the seller cannot reconstruct is a tier they will
  ignore.
