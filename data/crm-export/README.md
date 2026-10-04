# CRM export

The fallback when no CRM connector is configured. Several agents degrade to this
rather than failing silently.

Drop a CSV here named `opportunities.csv` with at least:

```
account_name, account_id, stage, amount, close_date, last_activity, owner
```

Contents are gitignored. See `SECURITY.md` — customer names and pipeline data
should not be committed to a public repo.
