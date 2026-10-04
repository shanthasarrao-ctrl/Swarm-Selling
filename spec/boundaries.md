# Boundaries

These are limits on the system, written as spec rather than buried in a README
so that widening them is a visible, reviewable act.

## Nothing sends

No agent in this repo has send capability. Not email, not LinkedIn, not CRM
writes. Agents draft. A human sends.

This is not a default. It is the design. If you add sending, you are building a
different thing and you should say so in your fork.

## Touch caps

Per account, per quarter:

| Tier | Cap |
| --- | --- |
| 1 | 6 |
| 2 | 8 |
| 3 | 4 |

Counted in `log/touches.tsv`. Tier 3 is lowest on purpose — volume accounts get
the least evidence behind each touch, so they earn the fewest.

An agent that finds a genuine reason to exceed a cap reports it and stops.

## Internal request caps

Deal desk, legal and solutions consultants are shared, scarce, and they
remember who wastes their time. There is no error signal here either — you will
simply find yourself queued behind colleagues who asked more carefully.

Per rep, per week:

| Request type | Cap |
| --- | --- |
| Deal desk / finance approval | 3 |
| Legal review | 2 |
| SC escalation | 5 |

Counted in `log/internal-requests.tsv`.

These caps exist because the agents make asking frictionless, and friction was
doing useful work. An agent that hits a cap reports it and stops.

## Interrupt budget

The orchestrator may surface at most **5 items per week** across the whole
territory. Not five per account. Five.

Every alerting system starts useful and becomes noise, at which point people
stop reading it and the whole thing is worse than nothing. Scarcity is what
keeps the output worth opening.

Most weeks, for most accounts, nothing has changed. Saying nothing is a correct
output.

## Cost ceiling

Scheduled runs stop at a configured spend limit and cancel remaining work rather
than completing it. Set it in `.github/workflows/weekly.yml`. You are paying for
this on your own key.

## Model assignment

| Work | Model |
| --- | --- |
| Research, extraction, dedupe | cheap |
| Orchestration, adjudication, quality gate | expensive |

## What this costs you

These limits make the system produce less. That is the intent. Preparation is
now abundant and buyer attention is not, so a system optimised for volume is
optimising against the only finite input in the process.
