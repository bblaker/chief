# State Directory

Runtime state files for routine delta tracking. Each routine that persists state writes a JSON file here.

## Format

Each file follows this structure:

```json
{
  "routine": "routine-name",
  "last_run": "ISO-8601 timestamp",
  "data": { ... }
}
```

## Retention

| Routine | File | Retention |
|---------|------|-----------|
| Daily Briefing | daily-briefing.json | Last run only |
| Stakeholder Pulse | stakeholder-pulse.json | 60 days |
| Governance Tracker | governance-tracker.json | Last run only |
| Staff Reviews | staff-reviews.json | 3 months |
| Budget Review | budget-review.json | 12 months |

Routines not listed here derive all data from live sources and do not persist state.

## Phase 2

When scheduled mode goes live, state moves from local JSON to remote storage (S3 or ClickUp doc). The file format stays the same.
