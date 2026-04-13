# Meeting Prep

## Trigger Phrases
"prep me for my [time] meeting", "prep me for [meeting name]", "what should I know before my call with [person]", "meeting prep"

## Schedule
Manual only. Ben triggers this conversationally. Automated scheduling (30min before Tier 1 meetings) is a future enhancement.

## MCP Servers
Calendar, ClickUp, Slack, Gmail

## Data Pulls

### Calendar
- Event details: title, time, attendees, description/agenda

### ClickUp
- Open items related to the meeting topic or assigned to attendees

### Slack
- Recent threads (last 7 days) involving attendees or the meeting topic

### Gmail
- Recent threads (last 7 days) with attendees

## Processing

1. Infer meeting topic from the title, description, and attendee mix
2. Surface unresolved items, open questions, and recent decisions relevant to the topic
3. Generate 3 talking points or questions Ben should raise
4. Flag pending asks from Ben to any attendee (things they're waiting on him for)

## Output (Structured)

```
## Prep -- [Event] @ [Time]

### Context
[1-2 sentences on what this is about]

### Open Items
- [item] -- [owner] -- [status]

### Talking Points
1. [point]
2. [point]
3. [point]

### They're Waiting on You
- [person] waiting on [thing] since [date]
```

## Output (Conversational)

Same info, tighter. "Your 2pm with Jon is about [X]. The main thing to raise is [Y]. He's been waiting on [Z] since Tuesday."

## State

None. Meeting prep is ephemeral and manual-only.
