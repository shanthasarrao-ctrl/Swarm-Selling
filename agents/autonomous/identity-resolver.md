---
name: identity-resolver
description: Maps a company name to domain, CIK, CRM id, LinkedIn slug and ATS. Runs once per account.
cadence: on-add
permission: autonomous
model: cheap
reversible: true
reads: []
writes: [accounts/<slug>.md]
requires: []
---

# Identity resolver

## Purpose

Fill the identity block in `accounts/<slug>.md`. Boring, and everything else
depends on it.

## Procedure

1. Resolve the company's primary domain from its own website.
2. If public, find the CIK via SEC full-text company search. Confirm the legal
   name matches — subsidiaries and similarly named registrants are the common
   failure.
3. Detect the applicant tracking system by checking for a careers page hosted on
   Greenhouse, Lever or Ashby. Record which. These expose public JSON and are
   the cheapest reliable source of hiring signal.
4. Record aliases: trading name, former name, common abbreviations.
5. Set `public: true|false`.

## Rules

- Never guess a CIK. A wrong one means every filing claim downstream is about a
  different company, stated with full confidence.
- If the legal entity is a subsidiary of a larger filer, record both and note
  which one files.
- If you cannot resolve the domain with certainty, stop and say so.

## Failure mode to avoid

Resolving to a similarly named company and proceeding. Every error after this
point inherits it and none of them look like errors.
