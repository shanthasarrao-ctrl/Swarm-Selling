# Spec metadata

This file is the contract. Read it before editing anything in `spec/`.

## The rule

`spec/` defines what good looks like. `agents/` acts. They are separate on
purpose, and the separation is the point: an agent that can edit its own
criteria has no criteria.

Nothing in `spec/` is edited while agents are running. Change it deliberately,
in its own commit, with a reason in the message.

## Every criterion carries

- `set:` the date it was written or last confirmed
- `evidence:` what it rests on — deal counts, call quotes, observed patterns
- `confidence:` strong / moderate / weak

A criterion without evidence is an opinion. Agents should weight it accordingly.

## Expiry

| Confidence | Re-confirm every |
| --- | --- |
| Strong | 12 months |
| Moderate | 6 months |
| Weak | 3 months |

`agents/periodic/criteria-maintenance.md` reports what has aged out. It does not
fix anything — expiry is a prompt for a human, not a task for an agent.

## Promotion

Patterns observed in `log/instincts.md` do not enter `spec/` automatically.
Threshold: four independent occurrences. Below that they are candidates and
should be labelled `confidence: weak` if used at all.

This is the guard against one bad quarter becoming permanent policy.

## Provenance

If this repo is public, `spec/` must contain nothing confidential to your
employer. Publicly observable positioning, your own anonymised post-mortems,
your own judgment. Not pricing sheets, not win/loss exports, not customer names.
