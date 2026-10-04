---
name: industry-analysis
description: Aggregates filing language across peer companies in a vertical to find shared, emerging pressure.
cadence: monthly
permission: autonomous
model: cheap
reversible: true
reads: [spec/pains.md, spec/icp.md, spec/freshness.md]
writes: [log/instincts.md]
requires: []
---

# Industry analysis

## Purpose

Run once per industry, reuse across every account in it. Forty accounts rarely
span more than five industries, which is why this is cheap.

The output nobody else produces: nine of twelve peers added the same risk factor
this year.

## Procedure

1. Identify 8–15 public companies in the vertical, comparable in scale.
2. Pull the two most recent annual filings for each.
3. Diff Item 1A year over year for every one.
4. Cluster the changes. Report only risks that appear in three or more companies
   — anything less is company-specific and belongs in account analysis.
5. For each cluster, state how many peers, which ones, and the direction of
   travel.
6. Map clusters to `spec/pains.md`. Note explicitly where a cluster maps to no
   pain you address. That gap is information, not a failure.

## Output

- Clusters, with peer counts and citations
- Which map to pains you remove, which don't
- What changed since the last run

## Rules

- Three-company minimum per cluster. Two is a coincidence.
- Cite the filing and section for every claim.
- Do not infer industry direction from press coverage. Filings only.

## Failure mode to avoid

Reporting that an industry faces "cost pressure" and "digital transformation".
Every industry does. Report only what changed.
