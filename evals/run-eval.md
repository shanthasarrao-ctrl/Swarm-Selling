# Evals

Ten frozen public companies. Known findings. A before-and-after for spec changes.

## Why

Nothing else here tells you whether an edit to `spec/` helped without waiting a
quarter for deals to close. This will not tell you if you will win more. It will
tell you if the research stack still finds what you know is there.

## Layout

```
evals/fixtures/<slug>.md      the account, frozen
evals/expected/<slug>.md      findings a good run should surface
```

## Choosing fixtures

- Public companies only, so filings are available and stable
- Companies you do not sell to, so nothing confidential appears
- A spread: two obvious fits, two obvious misses, six ambiguous
- Ambiguous cases carry the signal. Anyone can classify the obvious ones.

## Expected findings

Write what a competent human analyst would surface. Be specific — "cost pressure
in Item 1A" is not checkable; "new risk factor on service delivery costs, added
in FY25, not present FY24" is.

## Scoring

| Metric | Meaning |
| --- | --- |
| Hit | Expected finding surfaced |
| Miss | Expected finding not surfaced |
| **Invented** | Finding surfaced that is not in the filings |

Invented is the number that matters. An agent that hits ten of ten and invents
three is worse than one that hits eight and invents none, because you cannot
tell which three.
