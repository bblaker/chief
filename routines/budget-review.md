# Budget & Spend Review

## Trigger Phrases
"where's AWS spend", "budget review", "what are we spending on", "upcoming renewals", "Canopy savings"

## MCP Servers
Gmail, ClickUp

## Note on Data Gaps
AWS spend and vendor costs are not natively in Gmail or ClickUp. For v1, this routine relies on:
1. Email parsing: AWS billing alerts and vendor invoices that arrive via email
2. ClickUp: procurement tasks and budget line items

Future: CSV upload flow for AWS Cost Explorer exports and vendor spend sheets.

## Data Pulls

### Gmail
- Vendor invoices, renewal notices, procurement emails (last 30 days)
- AWS billing alerts or cost notification emails

### ClickUp
- Procurement tasks and budget items
- Canopy consolidation tracking items

## Processing

1. Month-over-month comparison where data is available. Flag >15% spikes per line item.
2. Track Canopy consolidation progress against the $150K target
3. Surface renewals or procurement decisions due in the next 30-60 days
4. Compare against previous state in `state/budget-review.json` for MoM deltas
5. Draft a one-page summary suitable for Jon or CFO/COO

## Output (Structured)

```
## Budget & Spend -- [Month]

### AWS
- Total: $[X] | MoM: [+/-]% | YoY: [+/-]%
- Spikes: [service] $[X] ([+/-]%) -- [cause if known]

### Software/SaaS
- Active: [N] subscriptions, $[X]/mo
- Canopy savings: $[X] of $150K target ([%])
- Renewals (next 60 days):
  - [vendor] -- $[X]/yr -- [date]

### Staffing
- Headcount: [actual] vs. [plan]
- Contractors: $[X]/mo

### Summary
[3-4 sentences for leadership]
```

Skip any section where data is unavailable. Note which sections lack data and why.

## Output (Conversational)

Answer the specific question. "Where's AWS spend?" gets the AWS section. "Upcoming renewals?" gets just the renewal list.

## State

After running, persist to `state/budget-review.json`:
```json
{
  "routine": "budget-review",
  "last_run": "ISO-8601 timestamp",
  "data": {
    "snapshots": {
      "2026-04": {
        "aws_total": 45000,
        "saas_monthly": 12000,
        "canopy_savings": 35000,
        "headcount_actual": 42,
        "headcount_plan": 45,
        "contractor_monthly": 18000
      }
    }
  }
}
```

Retention: 12 months. Prune entries older than 12 months on each write.
