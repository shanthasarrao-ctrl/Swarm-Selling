# CRM schema

Map your CRM's fields to the names agents expect. Agents read this file rather
than assuming a schema, because nobody's Salesforce looks like anybody else's.

| Agent expects | Your field | Object |
| --- | --- | --- |
| account_name | Name | Account |
| account_id | Id | Account |
| stage | StageName | Opportunity |
| amount | Amount | Opportunity |
| close_date | CloseDate | Opportunity |
| last_activity | LastActivityDate | Account |
| incumbent | *(custom)* | Account |
| contacts | Contact[] | Contact |

Agents never write to stage, amount, close date or forecast category. See
`agents/gated/crm-write.md`.
