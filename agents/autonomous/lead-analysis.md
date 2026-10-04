---
name: lead-analysis
description: Person-level qualification — seniority, tenure, function, likely authority.
cadence: weekly
permission: autonomous
model: cheap
reversible: true
reads: [spec/icp.md, spec/buyer-personas.md, spec/disqualifiers.md]
writes: [accounts/<slug>.md]
requires: []
---

# Lead analysis

## Purpose

Establish whether a named person is plausibly the right person, before anyone
spends effort writing to them.

## Procedure

1. Match the person's function against `spec/buyer-personas.md`.
2. Record seniority and time in seat. New executives in the 0–9 month window
   change things; executives at year six usually do not.
3. Assess likely budget authority for a purchase of your size. Be conservative.
4. Check `spec/disqualifiers.md` — champion below director with no executive
   access is a gate in `spec/scoring-model.md`, not a deduction.
5. Note who else at the account is already in the thread. Single-threaded is a
   risk to report, not a detail.

## Rules

- No scraping LinkedIn. It is against their terms, actively enforced, and any
  system built on it breaks the day they change something. Use what people
  publish elsewhere, or what your CRM already holds.
- Seniority is not authority. Record them separately.
- Do not infer personality, working style or receptiveness from a profile.

## Failure mode to avoid

Producing a confident read on a person from a job title and nothing else.
