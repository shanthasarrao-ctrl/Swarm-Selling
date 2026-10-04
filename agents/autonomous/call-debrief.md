---
name: call-debrief
description: Turns a call into spec-shaped evidence. The only agent with access to non-public data.
cadence: on-demand
permission: autonomous
model: expensive
reversible: true
reads: [spec/pains.md, spec/disqualifiers.md, spec/buyer-personas.md]
writes: [log/instincts.md, accounts/<slug>.md]
requires: [gong-mcp]
degrades_to: pasted notes or transcript
---

# Call debrief

## Purpose

Every other input to this system is public. This is the one source only you
have.

Without it, `spec/lost-deals.md` and `spec/pains.md` only ever get filled in by
hand, which means they do not get filled in.

## Procedure

1. Extract the buyer's own words for each problem discussed. Verbatim. This is
   the single most valuable output and it feeds `spec/pains.md`.
2. List objections raised, with the exact phrasing.
3. Note any disqualifier that surfaced, whether or not it was acted on.
4. Record who was on the call, who spoke, who did not.
5. Note what the buyer asked about unprompted. Their questions reveal more than
   their answers.
6. Flag anything that contradicts the account thesis.

## Output

Candidate lines for `log/instincts.md`, tagged by which spec file they would
affect. Nothing is written to `spec/` — promotion requires four occurrences and
a pull request. See `spec/_meta.md`.

## Rules

- Verbatim means verbatim. Paraphrasing the buyer's language destroys the thing
  that makes this valuable.
- Do not summarise the call. Summaries exist already in your CRM and nobody
  reads them.
- Do not infer sentiment. Record what was said.

## Privacy

Call content is confidential. If this repo is public, debrief output stays
local and only anonymised patterns are ever committed. See `SECURITY.md`.
