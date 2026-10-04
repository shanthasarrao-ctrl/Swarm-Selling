# Security

This is a public repository that people will fill with real pipeline data.
Someone will paste a call transcript into `accounts/` in the second week. This
file and the pre-commit hook exist for that person.

## Never commit

- Customer or prospect names, in any file
- Call recordings, transcripts, or notes quoting identifiable people
- Win/loss exports from your CRM
- Deal sizes tied to named accounts
- Your employer's pricing, discounting rules or margin structure
- Competitor pricing or anything obtained under NDA
- API keys, tokens, credentials, connector config with real values
- Contact details of any kind

## Gitignored by default

`accounts/*` (except the template), `data/crm-export/*`, `log/*.tsv`,
`log/sessions/`, `mcp-config/mcp-servers.json` if edited with real values.

The pre-commit hook in `.pre-commit-config.yaml` blocks the obvious cases. It
will not catch everything. It is a seatbelt, not a policy.

## Before you connect anything

Connecting Gong or Salesforce means your employer's customer data flows through
agents running on your machine, under your API key, possibly on a schedule.

That is a conversation with your own security team, not a configuration step.
Have it first. "I did not realise it was sending customer data anywhere" is not
a defence you want to rely on.

## If you work for a vendor in this space

Your competitive intelligence, win/loss data and battlecards are almost
certainly your employer's property, not yours. `spec/competitors.md` should
contain only publicly observable positioning. Your own anonymised post-mortems
are a greyer area and worth asking about before you publish anything.

## Reporting

Open an issue for repo problems. For anything involving leaked data in a public
fork, contact the fork owner directly first.
