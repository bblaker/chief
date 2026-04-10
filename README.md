# AI Chief of Staff

Conversational AI Chief of Staff that operates in two modes:

1. **Conversational** - Chat interface for questions, briefings, and actions. Routes to the right data sources (Gmail, Calendar, Slack, ClickUp, GitHub) and responds concisely.
2. **Scheduled** - Cron-driven routines delivered via Slack DM.

Both modes share the same system prompt, routine definitions, and MCP routing.

## Routines

| Routine | Schedule | Purpose |
|---------|----------|---------|
| Daily Briefing | Weekdays 7am MT | Calendar, comms, status changes, top 3 priorities |
| Decision Queue | Weekdays 8am MT | Items blocked on Ben, ranked by impact |
| Weekly Recap | Friday 4pm MT | What shipped, carryovers, draft CEO update |
| Dev Goals Check-in | Wednesday 9am MT | Board development areas, direct report deliverables |
| Stakeholder Pulse | Monday 9am MT | Last contact with key stakeholders, outreach flags |
| Governance Tracker | Monday 8:30am MT | Upcoming forums/committees, prep status |
| Staff Reviews | Monthly/Quarterly | Performance signals, 1:1 prep |
| Budget Review | 1st Wed of month | AWS, SaaS, staffing spend vs. plan |
| Meeting Prep | 30min before key meetings | Context, open items, talking points |

## Setup

```
npm install
npm run build
```

## Dev

```
npm run dev          # Run scheduler locally
npm run typecheck    # Type check
npm test             # Run tests
```

See `spec.md` for full specification.
