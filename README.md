# Swarm Selling

**Version-controlled sales judgment that agents can read.**

[swarmselling.com](https://swarmselling.com)

Your ICP lives in a deck from last year. Your competitive positioning is in a
call recording nobody will rewatch. The reason you actually lose deals is in
your best rep's head and it leaves when they do.

None of it is diffable. Nobody on your team can answer: what changed in our
targeting this quarter, what evidence caused the change, and did it help.

This is a specification layer that fixes that, plus the agents that read it.

---

## The problem it exists for

Sales has no error signal.

Write bad code and a test fails. That is why coding agents work — generate a
thousand changes, let an objective system reject the bad ones.

Bad qualification crashes nothing. A weak ICP throws no error. You can spend
three quarters targeting the wrong accounts while the dashboard looks perfectly
healthy, and bad judgment is indistinguishable from a soft market.

That was survivable while the judgment sat in someone's head. It stops being
survivable when agents act on it at volume, consistently, across every account
you own. AI does not only amplify good judgment. It industrialises bad judgment.

## Install

```bash
/plugin marketplace add shanthasarrao-ctrl/Swarm-Selling
/plugin install swarmselling@swarmselling
```

Or, for Cursor, Codex, Gemini CLI and others honouring `AGENTS.md`:

```bash
npx skills add shanthasarrao-ctrl/Swarm-Selling
```

Then:

```
/gtm-init      # the interview. Five minutes gets you a working minimum.
/gtm-check     # validates what you have
/gtm-brief <account>
```

**`/gtm-init` is not optional.** Every spec file ships with sample content from
a fictional vendor. Run the agents against it and you get a beautifully
formatted brief about nothing. The agents check for this and refuse to run.

## How it works

### Nine files hold the judgment

`spec/` — ICP, disqualifiers, pains in the buyer's words, competitors,
lost-deal post-mortems, buyer personas, voice, boundaries, territory.

Every claim carries three things a playbook never does: the evidence behind it,
a confidence level, and the date it was set. Strong claims re-confirm yearly,
weak ones quarterly. Expired criteria get flagged, because nothing else in sales
will tell you your targeting went stale.

### The spec is separate from the agents

Agents read `spec/`. Agents never write to it. An agent that can edit its own
criteria has no criteria.

Changes arrive as pull requests with evidence attached, and a pattern needs four
independent occurrences before it becomes a rule. One lost deal is an anecdote.

### Tiering splits public from private

```
Tier = Account Potential × Account Probability
```

Potential — industry health, revenue, growth, hiring, leadership, moat — is
publicly observable. An agent scores it.

Probability — exec connection, champion strength, relationship strength,
multithreading — is private to you. You score it.

Not a compromise. The system cannot fully tier an account by design, because
half the inputs are things only the person in the room knows.

### One line the agents do not cross

Some work is reversible. Research a filing, spot a hiring signal, prepare a
brief. Wrong costs an hour. Run it unsupervised at any volume.

Once something leaves the building — an email to a CIO, a CRM write, a submitted
forecast — the mistake is external and permanent. No model improvement fixes
that.

So the folders are permission levels. And **nothing in this repo can send.** It
drafts; you send. Touch caps per account live in `spec/boundaries.md` rather
than a README, so widening them is a visible act.

### The agents that argue

This is the part that does not exist elsewhere.

`competitor-rep` makes the incumbent's best case against your POV, using your
own lost-deal file — the arguments that have actually beaten you.

`buyer-adjudicator` hears both cases **blind**, without knowing which is yours,
and says which was more convincing. If it knows which is yours, it finds for
you. Every tool in this category flatters its operator.

`buying-committee` tests whether the argument survives being repeated. Your
champion has to carry it into a room you are not in, in three sentences, to
people who never met you. If it does not compress, it does not close.

`gap-analysis` splits the verdict. Positioning gaps — you had an advantage and
failed to make it legible — are yours to fix this week. Capability gaps go to
`log/gaps.tsv` with a count, so what reaches product is "this beat us nine
times" rather than an anecdote from Tuesday.

The adversarial round runs **before** drafting. If the case loses in simulation,
the fix is the argument, not the subject line.

### What the buyer already believes

`market-perception` is the only agent here that researches you rather than the
account. It runs the questions a buyer runs — category, comparison, verdict —
across search, review sites and AI assistants, and reports what comes back.

By the time someone takes a first call they have already asked an assistant
which tool is best and how you compare. That answer is the frame your argument
works against, and most sellers have never seen it.

It reports characterisations and their sources, never a visibility score.
Assistant outputs are non-deterministic and personalised; a number computed over
them is precision invented from noise.

### The internal tier

Deal desk, legal, SC and product. Gated on a different axis from the
customer-facing agents: the cost of getting these wrong is not a lost
relationship, it is your standing with colleagues whose time is shared and
scarce.

`deal-desk` assembles an approval package — the ask, the precedent, what it
buys, what happens if declined — so approval takes one pass instead of three.
It does not decide whether the discount is justified and it does not submit.

`legal-review` diffs redlines against your standard agreement and prepares the
question. It never states whether a term is acceptable. A model that tells a
seller a clause looks fine produces a confident answer with no authority behind
it, and the seller repeats it to the customer.

`solutions-consult` answers technical questions from documented sources with a
citation, or says it does not know and drafts the question for a human SC.
There is no third option. A hallucinated capability claim does not stay a
mistake — the customer writes it into requirements.

`product-liaison` runs the inbound direction nobody does well: filtering what
shipped against your own lost arguments, and naming the closed-lost deals now
worth reopening.

Internal request caps live in `spec/boundaries.md`. These agents make asking
frictionless, and friction was doing useful work.

### The agents that check

Every agent stack on the market produces something. None of them check
anything.

- `criteria-maintenance` reports what has expired
- `disconfirmation` hunts evidence that the ICP is wrong — accounts you won that
  the spec says you should have lost, disqualifiers sitting inside closed-won
  deals
- `quality-gate` catches contradictions between agents in the same run
- `win-loss-analysis` tests whether the scoring model actually separates deals
  you win from deals you lose, and diagnoses every Tier 1 loss as either a
  potential-side or probability-side failure
- `calibration` scores predictions against outcomes

None of them fix anything. They make a human look.

### Waves, not a list

Agents are a dependency graph. See `swarm/deal-swarm.yaml`.

```
1  identity
2  research            (parallel)
3  POV
4  adversarial         ← before drafting
5  draft               (gated by tier + rubric)
6  critique loop
7  quality gate
8  human
```

## What it deliberately does not do

**No self-improving loop.** Karpathy's autoresearch works because a cheap
objective test scores every attempt in minutes. You close a handful of deals a
year, each confounded by territory, timing and someone's mood. `calibration`
logs predictions against outcomes, but at that sample size it takes quarters and
may never be conclusive. Anyone selling you a self-improving sales agent is
selling the component that does not exist.

**No integrations.** Salesforce, Gong and email connect through MCP servers you
configure. Every agent declares what it needs and degrades explicitly without
it. The whole research and adversarial stack runs with zero connectors, because
that is the install-day experience for most people.

**No LinkedIn automation.** There is no sanctioned programmatic path. Drafts are
pasted.

**No numeric verdicts on deals.** No probability percentages, no scores out of
ten on a brief. The sample sizes do not support them and the precision makes a
guess harder to question rather than easier.

**No volume.** Preparation is now abundant; buyer attention is not. The
interrupt budget is five items per week across the whole territory. Most weeks,
for most accounts, the correct output is nothing.

## Costs

Runs on your own API key. `spec/boundaries.md` sets a spend ceiling that cancels
remaining work rather than completing it. Research runs on the cheap model,
adjudication and the quality gate on the expensive one. Run `/gtm-dry-run` to
see what a Monday costs before the first Monday.

## Before you connect anything

Connecting Gong or Salesforce means your employer's customer data flows through
agents on your machine, on a schedule. That is a conversation with your security
team, not a configuration step. See `SECURITY.md`.

Your competitive intelligence and win/loss data are almost certainly your
employer's property. `spec/competitors.md` should hold publicly observable
positioning only.

## Structure

```
spec/          judgment — dated, evidenced, version controlled
accounts/      per-account state; probability is human-only
agents/
  autonomous/  reversible, unsupervised
  adversarial/ attacks the case
  critique/    attacks the message
  gated/       externally consequential
  internal/    deal desk, legal, SC, product
  periodic/    portfolio-level and cadenced
  scoring/     separate; never sees a draft
commands/      /gtm-init, /gtm-check, /gtm-brief, /gtm-joust, /gtm-tier, ...
swarm/         wave graphs
evals/         ten frozen fixtures — did a spec change help?
log/           predictions, outcomes, touches, gaps, instincts
```

## License

MIT. Fork it, fill it with your own judgment, keep that part private.
