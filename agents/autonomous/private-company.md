---
name: private-company
description: The degraded research path for accounts with no filings. Says so, and lowers confidence accordingly.
cadence: weekly
permission: autonomous
model: cheap
reversible: true
reads: [spec/pains.md, spec/freshness.md]
writes: [log/instincts.md]
requires: []
---

# Private company analysis

## Purpose

Roughly half of most target lists is private. EDGAR covers none of it. Without
an explicit degraded path, agents produce thin output that looks exactly like
rich output, which is worse than producing nothing.

## What is available

- Job postings — the best remaining signal, often the only structured one
- Careers page copy, which describes priorities in the company's own words
- Funding announcements and investor pages
- Product changelogs, status pages, docs
- Review sites
- Executive interviews, podcasts, conference talks
- Regulatory filings in other jurisdictions where applicable

## What is not available

Risk factors. Audited financials. Management discussion. Earnings transcripts.
The year-over-year diff that makes public-company analysis worth doing.

## Procedure

1. State up front that this is a private company and the filing-based analysis
   does not apply.
2. Work the sources above against `spec/pains.md`.
3. Cap every claim at moderate confidence. Nothing here is audited.
4. Cap the whole brief at weak confidence if the only source is job postings.

## Rules

- Never estimate revenue. Third-party revenue estimates for private companies
  are guesses with a logo on them, and repeating one to a CFO ends badly.
- Never present a private-company brief in the same format as a public one
  without the confidence labels. The formats should not be mistakable.

## Failure mode to avoid

Producing a confident-sounding brief from a careers page and a funding round.
