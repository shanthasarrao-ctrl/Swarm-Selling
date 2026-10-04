# Scoring model

> Replace the weights. They are placeholders and should be argued about.

## Account Potential — agent-scored, public data only

| Factor | Weight | Source |
| --- | --- | --- |
| Industry health | 2 | sector growth, public commentary |
| Revenue scale | 2 | filings, public reporting |
| Growth rate | 3 | year-over-year, not level |
| Hiring signals | 2 | job postings in the function you sell into |
| Leadership quality | 1 | tenure, public track record |
| Moat / USP | 2 | market position, switching costs |
| Capital access | 1 | recent raises, cash position |

Each factor scored 1–5. Weighted sum, normalised to 0–100.

## Account Probability — human-scored, private

| Factor | Weight | Gate? |
| --- | --- | --- |
| Exec connection | 3 | no |
| Champion strength | 3 | **yes** |
| Relationship strength | 2 | no |
| Multithreading (3+ contacts) | 2 | no |
| Prior wins in similar accounts | 2 | no |
| Category need in this industry | 2 | no |
| Prior category purchase | 1 | no |

Each scored 1–5. Weighted sum, normalised to 0–100.

## Gates

Some factors are not scores. They are gates, and a gate that fails zeroes the
axis rather than deducting from it.

- **No identified budget owner after two calls** → probability = 0
- **Champion has no executive access and none is obtainable** → probability = 0
- Any hard disqualifier in `spec/disqualifiers.md` → account = 0

Summing everything is how a fatal flaw gets averaged away by five mediocre
positives. Gates stop that.

## Final

```
Tier score = (Potential / 100) × (Probability / 100) × 100
```

Thresholds in `spec/territory.md`.

## Confidence

Weights carry the same metadata as everything else in `spec/`.

- `set: 2026-01-15` · `evidence: placeholder — replace before use`
- `confidence: weak` until you have re-derived them from your own closed-won set

Unweighted addition says exec connection matters as much as leadership
reputation. It does not. Argue about the weights; that argument is the value.
