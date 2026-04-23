# Daily Briefing

## Trigger Phrases
"daily briefing", "what do I need to know", "morning briefing", "catch me up", "what's on my plate"

## MCP Servers
Gmail, Calendar, Slack, ClickUp (GitHub TODO)

## Data Pulls

### Calendar (gcal)
- All events for today and tomorrow
- Flag: conflicts (overlapping times), back-to-backs with <15min prep gaps, events with Tier 1 attendees

### Gmail
- Unread and unreplied threads from the last 24 hours
- Rank by sender tier:
  - Tier 1: Jon, Tiffany, Brett (CEO/board) -- surface first
  - Tier 2: Chase, Ashley, Oki, Mason (direct reports) -- surface second
  - Tier 3: everyone else -- only surface if actionable

### Slack
- Unread DMs and @mentions

### ClickUp
- Tasks with status changes in the last 24 hours (on tasks Ben owns or watches)
- Overdue tasks across direct reports' teams
- Compare against previous state in `state/daily-briefing.json` to identify deltas
- **Migration RAID snapshot** (list ID: `901113562085` in Technology > Product Roadmap > Migration RAID):
  - Total open items (any non-closed/done status)
  - New items created in the last 24 hours
  - Items completed/closed in the last 24 hours
  - Use `clickup_filter_tasks` with list_ids `["901113562085"]` for open items, and `clickup_search` with location subcategories filter + created_date_from/to for new items, and task_statuses `["done", "closed"]` + sort by updated_at desc for recently completed

### GitHub (TODO)
- Open PRs requesting Ben's review, failed CI, notable merges (last 24h)
- Skipped until GitHub MCP is available

## Processing

1. Flag calendar conflicts and prep gaps
2. Rank all communications by sender tier, then by age
3. Compare ClickUp task statuses against yesterday's snapshot (from state file). Call out what changed.
4. Synthesize "Top 3 to close today" ranked by urgency and downstream impact

## Output (Structured)

When Ben explicitly asks for the full briefing:

```
## Daily Briefing -- [Date]

### Calendar
- [time] [event] [flag: conflict / no prep gap / key attendee]
- Tomorrow: [key events to prep for]

### Needs Response
| Priority | Source | From | Subject/Thread | Waiting Since |
|----------|--------|------|----------------|---------------|

### Status Changes (since yesterday)
- [item]: [old] -> [new] ([owner])

### Overdue
- [item] -- [owner] -- [days overdue]

### Migration RAID
- Open: [N] | New (24h): [N] | Closed (24h): [N]
- [If new or closed items exist, list them briefly]

### PRs/CI (TODO -- GitHub MCP)
- [repo]: [PR title] -- waiting [N] days
- [repo]: CI failing on [branch]

### Top 3 Today
1. [action] -- [why]
2. [action] -- [why]
3. [action] -- [why]
```

Skip any section that has no items. Do not include empty tables.

## Output (Conversational)

When Ben asks casually ("catch me up", "what's on my plate"):
- Lead with the most important thing
- Condensed prose, not tables
- Skip empty sections entirely
- Keep it to a few paragraphs max

## State

After running, persist to `state/daily-briefing.json`:
```json
{
  "routine": "daily-briefing",
  "last_run": "ISO-8601 timestamp",
  "data": {
    "clickup_statuses": { "task_id": "status" },
    "top_3": ["item 1", "item 2", "item 3"]
  }
}
```

Retention: last run only. Each run overwrites the previous state.
