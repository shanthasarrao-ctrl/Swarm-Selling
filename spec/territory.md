# Territory

> Replace the sample tiers and account list. The structure is the point.

Tier decides what runs, how often, and whether a human approves. It is the root
of the whole system.

## The model

```
Tier = Account Potential  ×  Account Probability
```

Multiplication, not addition. An account with enormous potential and no path in
is not a good account. Addition would let one axis hide the other.

**Potential** is publicly observable — industry health and account health.
An agent scores it. See `agents/autonomous/potential-scorer.md`.

**Probability** is private to you — exec connection, relationship strength,
multithreading, prior wins in similar accounts. You score it. No agent may.

That split is deliberate. The system cannot fully tier an account on its own,
because half the inputs are things only the person in the room knows.

Weights, gates and thresholds live in `spec/scoring-model.md`.

## Tiers

### Tier 1 — strategic

`score >= 70`

- Every outbound artifact reviewed by a human before it leaves, regardless of
  how clean the evidence looks
- Full research stack weekly
- Adversarial round on every POV
- Touch cap: 6 per quarter

These are accounts where a wrong send costs something built over years. The
rubric does not override this.

### Tier 2 — core

`score 40–69`

- Gate decided by `spec/intent-rubric.md`. Above threshold with a clean
  citation, the agent drafts and queues. Below it, a human reads first.
- Research stack weekly
- Adversarial round on new POVs
- Touch cap: 8 per quarter

### Tier 3 — volume

`score < 40`

- Agent proceeds without per-message review
- Research monthly, not weekly
- No adversarial round
- Touch cap: 4 per quarter

**Tier 3 still cannot send.** Nothing in this repo has send capability. See
`spec/boundaries.md`.

## Assignment

Per-account tier lives in `accounts/<slug>.md`, not here. This file holds
definitions and thresholds only — one source of truth per fact.

Tier changes are logged to `log/tier-history.tsv` so you can eventually ask
whether your tiering predicted anything.

## Review cadence

Re-tier quarterly, or when an account's probability inputs change materially
(champion leaves, exec connection made, competitor displaces you).
