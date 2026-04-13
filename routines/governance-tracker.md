# Governance Cadence Tracker

## Trigger Phrases
"when's the next tech committee", "governance tracker", "ELT forum status", "is the deck ready for [meeting]"

## MCP Servers
Calendar, ClickUp, Gmail

## Data Pulls

### Calendar
- Next ELT Technology Alignment Forum date
- Next Technology Committee date

### ClickUp
- Action items from the last session of each governance meeting
- Status of those action items (open vs. closed)

### Gmail
- Pre-read or agenda distribution status (has it been sent?)

## Processing

1. Calculate days until next session for each governance meeting
2. Determine agenda/deck status: drafted, not started, or sent
3. Tally prior action items: how many open vs. closed
4. Flag prep tasks that need to happen this week

## Output (Structured)

```
## Governance Cadence -- [Date]

### ELT Technology Alignment Forum (Monthly)
- Next: [date] ([N] days)
- Agenda: [status]
- Prior actions: [N] open / [N] closed
  - [open item] -- [owner]

### Technology Committee (Bi-weekly)
- Next: [date] ([N] days)
- Agenda: [status]
- Prior actions: [N] open / [N] closed
  - [open item] -- [owner]

### Prep This Week
- [ ] [task]
```

## Output (Conversational)

Answer the specific question asked. "When's the next tech committee?" gets a date and prep status, not the full tracker.

## State

After running, persist to `state/governance-tracker.json`:
```json
{
  "routine": "governance-tracker",
  "last_run": "ISO-8601 timestamp",
  "data": {
    "elt_forum": { "next_date": "2026-04-25", "agenda_status": "not_started", "open_actions": 3, "closed_actions": 5 },
    "tech_committee": { "next_date": "2026-04-18", "agenda_status": "drafted", "open_actions": 1, "closed_actions": 4 }
  }
}
```

Retention: last run only.
