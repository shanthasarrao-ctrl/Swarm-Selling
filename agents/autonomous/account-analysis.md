---
name: account-analysis
description: Reads a public company's filings against spec/ and reports where the thesis holds and where it fails. Runs weekly, unsupervised.
cadence: weekly
permission: autonomous
reversible: true
reads: [spec/icp.md, spec/pains.md, spec/disqualifiers.md]
writes: [log/instincts.md]
---

# Account analysis

## Purpose

Test one account against the specification. Not to summarise the company —
anyone can get a summary. To answer whether the pains in `spec/pains.md` are
visible in what this company publishes about itself, and whether anything in
`spec/disqualifiers.md` is present.

## Why this is autonomous

Output is internal and reversible. A wrong read costs an hour of reading, not a
relationship. Run it on every account, every week, without asking.

## Sources, in order of value

1. **10-K Item 1A (risk factors)** — the company's own list of what it fears,
   written under legal obligation. Diff against the prior year: a new risk, a
   risk that moved up the ordering, or language that intensified is worth more
   than the risk itself.
2. **Earnings call transcripts** — what executives say under questioning.
3. **Job postings** — the best available signal of what they have decided to
   fix. Who they hire reveals the priority.
4. **Changelogs, status pages, support docs** — what is breaking.
5. **Review sites** — where customers say it is breaking.

Skip press releases. Everyone's competitor already read those.

## Procedure

1. Read `spec/pains.md` and note the buyer's language for each pain, not the
   product category.
2. Retrieve the last two annual filings. Diff Item 1A.
3. Search each source above for the buyer's language from step 1.
4. For each pain: state whether evidence exists, cite the source and location,
   and rate the evidence strong / weak / absent.
5. Search for disqualifiers with equal effort. Report them even when the
   account otherwise looks good.
6. State the strongest argument that this account is **not** a fit. If you
   cannot make one, say so explicitly — that is itself a finding.

## Output

A brief of at most one page:

- Thesis: fits / partially fits / does not fit, in one sentence
- Evidence for, with a citation per claim
- Evidence against, with a citation per claim
- Disqualifiers present
- What changed since the last run

## Rules

- **Every claim carries a citation to filing and location.** A claim you cannot
  cite does not go in the brief. A rep repeating an uncited claim to a CFO has a
  problem no amount of fluency fixes.
- Do not infer a pain from a product category. Infer it from the company's words.
- Do not write to `spec/`. Candidate patterns go to `log/instincts.md`.
- If the account is private, say so and stop. Filings-based analysis does not
  apply and pretending otherwise produces confident fiction.

## Failure mode to avoid

Producing something for every account every week. Most weeks, for most accounts,
nothing has changed. Saying so is the correct output. A brief that exists to
justify the run is noise, and noise is how these systems get ignored.
