# Agent instructions

Read this before doing anything in this repository. It is read by Claude Code,
Cursor, Codex, OpenCode and anything else honouring the AGENTS.md convention.

## The contract

1. **`spec/` is read-only to you.** Agents read the specification. Agents never
   write to it. An agent that can edit its own criteria has no criteria.
   Candidate patterns go to `log/instincts.md` and reach `spec/` only through a
   pull request, after four independent occurrences.

2. **The probability section of any account file is read-only to you.**
   Exec connection, champion strength, relationship strength, multithreading —
   these are private to the human. Guessing at them from public data invents the
   most consequential number in the system.

3. **Nothing sends.** No agent in this repo has send capability. Not email, not
   LinkedIn, not CRM writes. You draft. A human sends. This is not a default
   setting; it is the design.

4. **Every factual claim carries a citation and an as-of date.** A claim you
   cannot cite does not go in the output, however true it feels.

5. **Check `spec/` for placeholder content before running.** This repo ships
   with sample content in every spec file. If it is still there, stop and tell
   the user to run `/gtm-init`. Producing a confident brief from a fictional
   vendor's ICP is the most likely way this repo wastes someone's afternoon.

6. **Silence is a valid output.** Most weeks, for most accounts, nothing has
   changed. Say so. Do not manufacture a finding to justify a run.

## Where things live

| Path | What |
| --- | --- |
| `spec/` | Judgment. Yours to read, never to write. |
| `accounts/` | Per-account state. Potential is yours; probability is not. |
| `agents/autonomous/` | Reversible. Nothing leaves the building. |
| `agents/adversarial/` | Attacks the case before anyone drafts a message. |
| `agents/critique/` | Attacks the message before a human sees it. |
| `agents/gated/` | Externally consequential. Tier and rubric set the gate. |
| `agents/internal/` | Colleagues' time. Capped, human submits. |
| `agents/periodic/` | Portfolio-level and cadenced. |
| `agents/scoring/` | Separate on purpose. Never sees a draft. |
| `log/` | Predictions, outcomes, touches, instincts. Append-only in spirit. |
| `swarm/` | Wave graphs. Agents are a dependency graph, not a list. |

## Reading order for a new run

1. `spec/_meta.md` — the contract for how criteria are dated and promoted
2. `spec/territory.md` — tier decides everything downstream
3. `spec/boundaries.md` — caps, budget, interrupt limit
4. The specific spec files your agent declares in `reads:`

## Frontmatter fields

Every agent declares:

- `permission:` autonomous | gated
- `cadence:` weekly | monthly | quarterly | daily | on-demand | per-run
- `model:` cheap | expensive
- `reversible:` true | false
- `depends_on:` which agents must complete first
- `reads:` / `writes:` which files
- `requires:` / `degrades_to:` connectors, and behaviour without them

If a connector in `requires:` is unavailable, follow `degrades_to:` and say
explicitly in the output that you are running degraded, with reduced confidence.
Never fail silently.
