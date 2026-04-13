# Staff/Performance Reviews

## Trigger Phrases
"how's [person] doing", "staff pulse", "team performance", "prep me for my 1:1 with [person]", "quarterly review prep"

## MCP Servers
ClickUp, Slack, Calendar (GitHub TODO)

## Direct Reports Tracked
- Chase Pierce: VP of Software Engineering
- Ashley Murray: Sr. Director of Product Management
- Oki: Director of IT
- Mason: Sr. Manager of Data Engineering
- 4 Engineering Managers (report to Chase)
- 6 Product Managers (report to Ashley)

## Monthly Pulse

### Data Pulls
- ClickUp: task completion per person (last 30 days vs. prior 30 days)
- GitHub (TODO): PR volume, review turnaround (technical leads). Skipped until GitHub MCP is available.
- Slack: activity patterns (volume, responsiveness)
- Calendar: 1:1 attendance with Ben

### Processing
- Per person: output trend (up/down/flat) based on task completion delta
- Flag anyone with >20% shift in either direction
- Flag missed 1:1s or declining engagement signals

### Output (Structured)

```
## Staff Pulse -- [Month]

| Person | Role | Output Trend | Notable Signal | Suggested Action |
|--------|------|-------------|----------------|------------------|

### Flags
- [person] -- [signal] -- [action]
```

## Quarterly Deep Review

### Data Pulls
- 3 months of pulse data (from `state/staff-reviews.json`)
- OKR/goal progress from ClickUp
- Ben's own notes (if stored in state)

### Processing
- Structured 1:1 prep doc per direct report
- Accomplishments, concerns, development areas, conversation starters
- Ashley: include a dedicated VP-readiness section assessing progress on her four deliverables

### Output (Structured, per person)

```
## Quarterly Review Prep -- [Person]

### Accomplishments
- [item]

### Concerns
- [item]

### Development Areas
- [area] -- [progress]

### Conversation Starters
1. [topic]
```

## Output (Conversational)

"How's Chase doing?" gets a 3-4 sentence answer pulling the latest signals. Not a full report unless asked. "Prep me for my 1:1 with Oki" gets talking points and recent signals for Oki specifically.

## State

After running, persist to `state/staff-reviews.json`:
```json
{
  "routine": "staff-reviews",
  "last_run": "ISO-8601 timestamp",
  "data": {
    "signals": {
      "Chase Pierce": {
        "2026-04": { "clickup_completed": 23, "slack_activity": "normal", "1on1_attended": true },
        "2026-03": { "clickup_completed": 19, "slack_activity": "normal", "1on1_attended": true }
      }
    }
  }
}
```

Retention: 3 months. Prune entries older than 3 months on each write.
