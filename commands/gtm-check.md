---
name: gtm-check
description: Validates the spec before anything runs. Reports gaps, expiry and leftover placeholders.
---

# /gtm-check

Validate `spec/` and report. Change nothing.

## Checks

1. **Placeholder text.** Every shipped template contains sample content. If any
   remains, the spec is not populated and every agent reading it will produce a
   confident brief about a fictional vendor. Report this first and loudly.
2. **Empty files.** Which spec files have no content.
3. **Missing metadata.** Criteria with no `set:` date, no `evidence:`, or no
   `confidence:`.
4. **Expiry.** Apply the table in `spec/_meta.md`. Report what has aged out.
5. **Contradictions.** A criterion in one file conflicting with another.
6. **Account files.** Missing identity blocks, missing tiers, probability
   sections left unscored.
7. **Connectors.** Which are configured, which agents degrade without them.

## Output

```
BLOCKING     placeholder content in spec/icp.md, spec/pains.md
WARNING      3 criteria expired (oldest: spec/competitors.md, set 2025-11-02)
WARNING      spec/voice.md empty — rewrite loop will produce generic prose
INFO         no CRM connector — deal-management degrades to data/crm-export/
OK           12 accounts tiered, 2 missing probability scores
```

## Rule

Report only. Do not fix, do not fill in, do not propose values.
