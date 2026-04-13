# Decision Queue

## Trigger Phrases
"who's waiting on me", "what's blocked on me", "decision queue", "what do I need to unblock", "my blockers"

## MCP Servers
Gmail, Slack, ClickUp (GitHub TODO)

## Cross-Routine Awareness
If the Daily Briefing ran earlier today, reference items already surfaced there rather than repeating them in full. Focus on net-new items and deeper decision context (who's stalled, what's the downstream impact).

## Data Pulls

### ClickUp
- Tasks in blocked/waiting status where Ben is the blocker or approver

### Gmail
- Threads with explicit asks directed at Ben where Ben has not replied

### Slack
- DMs and @mentions with unanswered questions or requests

### GitHub (TODO)
- PRs awaiting Ben's review
- Skipped until GitHub MCP is available

## Processing

1. Deduplicate across sources. If the same decision appears in both email and Slack, show it once and note both sources.
2. Rank by downstream impact (how many people/tasks are stalled) and wait time.
3. Split into two groups:
   - **Decide Now**: waiting >48 hours OR high downstream impact
   - **Decide This Week**: everything else

## Output (Structured)

```
## Decision Queue -- [Date]

### Decide Now
| Source | From | Ask | Waiting Since | Downstream Impact |
|--------|------|-----|---------------|-------------------|

### Decide This Week
| Source | From | Ask | Waiting Since |
|--------|------|-----|---------------|
```

Skip any section that has no items.

## Output (Conversational)

"You have [N] things blocked on you. The most urgent is [X] from [person], waiting [N] days. [Impact]. Want me to draft a response?"

## State

Retention: last run only. No persistent state needed -- all data is derived from live sources.
