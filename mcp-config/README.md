# Connectors

This repo ships the specification and the agents. Connectors are yours.

There is no Salesforce integration in here and there never will be. Auth, field
mapping, API limits and permissions are per-organisation problems that cannot be
solved from a public repo, and shipping one would mean maintaining it forever.

## The layering

```
spec/         your judgment          ← this repo
agents/       procedures             ← this repo
mcp-config/   declarations           ← this repo (config only)
connectors    your accounts          ← never in this repo
```

## What each unlocks, and what degrades without it

| Connector | Unlocks | Without it |
| --- | --- | --- |
| Salesforce | `deal-management`, `forecasting`, `crm-write` | Falls back to `data/crm-export/` |
| Gong | `call-debrief` | Paste notes or a transcript by hand |
| Gmail / Outlook | Thread context for follow-ups | `followup-sequencer` uses `log/touches.tsv` only |
| LinkedIn | *nothing* | There is no sanctioned programmatic path. Drafts are pasted. |

## Free sources needing no connector

EDGAR (filings), Greenhouse / Lever / Ashby (job postings as public JSON), RSS,
company changelogs and status pages. Most of the research stack runs on these
alone.

## The repo must work with zero connectors

That is the install-day experience for most people. Account analysis, industry
analysis, POV finder, competitive intel and the whole adversarial round need
nothing configured.

Every agent declares `requires:` and `degrades_to:` in its frontmatter. An agent
that fails quietly because a connector is missing is worse than one that says
"running without pipeline data, confidence reduced."

## The conversation to have first

Connecting Gong and Salesforce means your employer's customer data flows through
agents running on your machine. That is a security conversation with your own
company, not a repo setting. Have it before you configure anything.
