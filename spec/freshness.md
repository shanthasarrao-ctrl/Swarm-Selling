# Freshness

Every claim in a brief carries an as-of date. Past its window, it is discounted
rather than dropped — and labelled, so a brief never silently blends fresh and
rotten evidence.

| Source | Window | Notes |
| --- | --- | --- |
| 10-K / annual filing | 12 months | 15 months stale by the end of its cycle |
| 10-Q / quarterly | 4 months | |
| Earnings call transcript | 4 months | |
| Job postings | 6 weeks | Roles get filled or quietly pulled |
| Press / news | 2 weeks | Everyone's competitor already read it |
| Changelog / status page | 8 weeks | |
| Review sites | 6 months | Slow-moving, low precision |
| Exec appointment | 9 months | The window in which a new exec changes things |
| Your own call notes | 90 days | People and priorities move |

## Rules

- A brief states the as-of date beside each claim, not once at the top.
- Evidence past its window is marked `stale` and drops to weak confidence.
- Two sources past their window do not add up to one fresh source.
- `agents/autonomous/signal-dedupe.md` suppresses anything already surfaced,
  so the same risk factor does not arrive every Monday for a year.
