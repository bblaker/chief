# Weekly Recap

## Trigger Phrases
"weekly recap", "what shipped this week", "week in review", "summarize the week", "draft Jon update"

## MCP Servers
Gmail, Calendar, Slack, ClickUp (GitHub TODO)

## Data Pulls

### ClickUp
- Tasks completed this week across Engineering, Product, IT, Data Engineering
- Tasks that were planned/in-progress but not completed

### Calendar
- Meeting volume and distribution for the week

### GitHub (TODO)
- Merged PRs, releases/deploys
- Skipped until GitHub MCP is available

### Gmail + Slack
- Scan for new commitments made during the week. Look for phrases like "I'll", "we'll", "action item", "by Friday", "will do", "committed to"

## Processing

1. Categorize completions by team: Engineering, Product, IT, Data
2. Identify carryovers with reason (blocked, deprioritized, no update)
3. Extract new obligations/commitments Ben made
4. Draft weekly update to Jon covering: Aspyn stabilization, roadmap progress, staffing, anything needing CEO visibility. Write in Ben's voice (confident, concise, technically credible, no filler).

## Output (Structured)

```
## Weekly Recap -- Week of [Date]

### Shipped
- Engineering: [items]
- Product: [items]
- IT: [items]
- Data: [items]

### Carryovers
- [item] -- [reason] -- [new target]

### New Commitments
- [commitment] -- [source] -- [due]

### Draft Update to Jon
[3-5 bullets in Ben's voice]
```

Skip any section that has no items.

## Output (Conversational)

Lead with headline stats ("X items shipped, Y carried over"), then the Jon draft. Offer to send it.

## State

Retention: 1 week. No persistent state needed -- all data is derived from live sources for the current week.
