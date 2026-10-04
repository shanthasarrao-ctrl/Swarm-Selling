---
slug: acme-corp
tier: null                 # set by /gtm-tier — never edited by an agent
tier_score: null
last_tiered: null
---

# Acme Corp

## Identity

Filled once by `agents/autonomous/identity-resolver.md`. Everything downstream
keys off this block. "Acme Corp" and "Acme Corporation Inc." are different
strings and nothing works until this is right.

- `legal_name:`
- `domain:`
- `cik:`                    # SEC identifier; blank if private
- `crm_id:`
- `linkedin_slug:`
- `aliases: []`
- `public: true|false`
- `ats:`                    # greenhouse | lever | ashby | other — for job postings

## Potential — agent-scored

Public data only. See `spec/scoring-model.md`.

| Factor | Score | Evidence | As of |
| --- | --- | --- | --- |
| Industry health | | | |
| Revenue scale | | | |
| Growth rate | | | |
| Hiring signals | | | |
| Leadership | | | |
| Moat | | | |
| Capital access | | | |

**Potential: __ / 100**

## Probability — human-scored

Private. No agent may write below this line.

| Factor | Score | Note | Gate |
| --- | --- | --- | --- |
| Exec connection | | | |
| Champion strength | | | **gate** |
| Relationship strength | | | |
| Multithreading | | | |
| Prior similar wins | | | |
| Category need | | | |
| Prior category purchase | | | |

**Probability: __ / 100**

## Current state

- `stage:`
- `incumbent:`
- `last_touch:`
- `touches_this_quarter:`

## Thesis

One paragraph. Why this account has the problem you remove, in their words.

## Evidence against

The strongest case that this is not a fit. If you cannot make one, say so —
that absence is itself a finding.
