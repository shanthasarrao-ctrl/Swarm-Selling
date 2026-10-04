---
name: gtm-joust
description: Runs the adversarial round alone, against a POV you already have.
---

# /gtm-joust <account-slug>

Run waves 4 only: `competitor-rep`, `buyer-adjudicator`, `gap-analysis`.

Use when you already have a point of view — from the system or from your own
head — and want it attacked before you take it into a room.

## Procedure

1. Take the POV from the account file, or accept one pasted in.
2. `competitor-rep` builds the incumbent's best case, using
   `spec/lost-deals.md` for arguments that have actually beaten you.
3. Present both cases to `buyer-adjudicator` blind, in randomised order.
4. `gap-analysis` splits the verdict into positioning and capability.

## Output

- Which case was more convincing, and on what grounds
- What would move the verdict
- What neither case addressed
- Positioning gaps: what you should have said
- Capability gaps: logged to `log/gaps.tsv` with a count

## Rule

The adjudicator must not be told which case is yours. If you are pasting a POV
in manually, do not label it.
