# Development Goals Check-in

## Trigger Phrases
"how am I tracking on my goals", "development goals", "how's Ashley tracking", "check on Ashley's deliverables", "board development areas"

## MCP Servers
ClickUp, Gmail, Slack, Calendar

## Data Pulls

### ClickUp
- Items tagged to Ben's nine board-provided development areas
- Ashley's four VP deliverables:
  1. PM operating model
  2. Team assessment with expected cuts
  3. Product success metrics
  4. AI adoption/reskilling plan

### Calendar
- Meetings related to development areas (last 14 days)

### Slack/Gmail
- Threads related to development areas or Ashley's deliverables

## Processing

1. Per development area: find last activity, flag if stale (14+ days with no activity)
2. Ashley's deliverables: calculate days to April 30 deadline, last activity, risk assessment (on track / at risk / behind)
3. Flag anything drifting without a clear owner

## Output (Structured)

```
## Development Goals -- [Date]

### Ben's Board Development Areas
| # | Area | Last Activity | Days Since | Status | Next Action |
|---|------|--------------|------------|--------|-------------|

### Ashley's VP Deliverables (Due: April 30)
| Deliverable | Days Left | Last Activity | Risk | Notes |
|-------------|-----------|---------------|------|-------|

### Ownership Gaps
- [item] -- no clear owner -- last touched [date]
```

Skip any section that has no items.

## Output (Conversational)

Focus on whatever Ben asked about. If he asks about Ashley, answer about Ashley. Do not dump all nine board areas unless he asked for them.

## State

Retention: last run only. No persistent state needed -- all data is derived from live sources.
