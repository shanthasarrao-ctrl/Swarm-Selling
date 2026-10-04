# Contributing

Two different things happen in this repo, and they have different rules.

## Changing your own spec

If you have forked this to run your own territory, `spec/` is yours. The rules
below are what makes a spec trustworthy over time, but nobody is enforcing them
except you.

### The four-occurrence rule

A pattern becomes a criterion after **four independent occurrences**. Below
that, it lives in `log/instincts.md` as a candidate.

One lost deal is an anecdote, usually with more than one explanation. The
fastest way to wreck a specification is letting a bad quarter rewrite it.

### Every spec change is a pull request

Not a Slack message, not an edit on main. The PR template asks for evidence,
occurrence count and confidence, because the review is the point — a criterion
nobody had to defend is a criterion that will quietly rot.

### Team mode

Shared state lives in the repo. Spec changes arrive as PRs. One person — usually
RevOps — approves.

Reps annotate their own account files. Reps do not fork the spec. Two versions
of the ICP is the failure this whole structure exists to prevent, and it happens
within a quarter if you let it.

## Contributing to the project itself

Useful contributions, roughly in order:

1. **Agents that check rather than produce.** The repo is deliberately short of
   these and they are the hardest to write well.
2. **Eval fixtures.** Public companies with well-documented findings.
3. **Degraded paths.** Private companies, missing connectors, non-US filings.
4. **Corrections.** Places where an agent's instructions produce confident
   nonsense.

Less useful:

- More producing agents. There are enough.
- Sending capability. Not a feature gap; see `spec/boundaries.md`.
- LinkedIn automation. Will not be merged.
- Numeric verdicts, confidence percentages, probability scores on deals. The
  sample sizes do not support them and the precision makes guesses harder to
  question.

### Never commit

Your populated `spec/`, your `accounts/`, your CRM export, call transcripts, or
anything else in `SECURITY.md`. The templates are the contribution; your
judgment is yours.
