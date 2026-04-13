# Stakeholder Pulse

## Trigger Phrases
"when did I last talk to [person]", "stakeholder pulse", "who haven't I talked to", "relationship check"

## MCP Servers
Slack, Gmail, Calendar

## Tracked Stakeholders
- Jon: CEO, Ben's direct manager
- Tiffany Hagge: Board Chair (Citation)
- Brett: Board, equity/MIP contact
- Chase Pierce: VP of Software Engineering
- Ashley Murray: Sr. Director of Product Management
- Oki: Director of IT
- Mason: Sr. Manager of Data Engineering

## Data Pulls

### Calendar
- Meetings with tracked stakeholders (last 14 days)

### Gmail
- Email threads with tracked stakeholders (last 14 days)

### Slack
- DMs and channel interactions with tracked stakeholders (last 14 days)

## Processing

1. Per stakeholder: find the last meaningful touchpoint, how many days ago, and which channel (email, Slack, calendar)
2. Flag anyone 14+ days without contact
3. Scan team Slack channels for anomalies (unusual quiet, escalation spikes, high volume)
4. Compare against previous state in `state/stakeholder-pulse.json` if available

## Output (Structured)

```
## Stakeholder Pulse -- [Date]

| Person | Role | Last Contact | Channel | Days Since |
|--------|------|-------------|---------|------------|

### Needs Outreach
- [person] -- [N] days -- [suggested action]

### Team Channel Signals
- [channel]: [observation]
```

Skip any section that has no items.

## Output (Conversational)

If asked about a specific person ("when did I last talk to Tiffany?"), answer for that person only. If asked generally, lead with who needs attention.

## State

After running, persist to `state/stakeholder-pulse.json`:
```json
{
  "routine": "stakeholder-pulse",
  "last_run": "ISO-8601 timestamp",
  "data": {
    "touchpoints": {
      "Jon": { "last_contact": "2026-04-10", "channel": "calendar", "summary": "1:1 meeting" }
    }
  }
}
```

Retention: 60 days. Prune touchpoint entries older than 60 days on each write.
