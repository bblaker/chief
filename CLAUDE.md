# AI Chief of Staff

Executive assistant skill + scheduler for Ben (Head of Technology, Aptive Environmental).

## Architecture

Two modes sharing the same routines and system prompt:
- **Conversational**: Claude skill triggered by chat. Routes to MCP servers based on intent.
- **Scheduled**: Claude remote triggers run routines on cron, deliver via Slack DM.

Key files:
- `SKILL.md` - Skill entry point (routing logic, MCP config)
- `system-prompt.md` - Base persona and org context
- `routines/` - Markdown routine definitions (one per file, self-contained)
- `scheduler/config.yaml` - Cron definitions for Phase 2 remote triggers
- `state/` - JSON files for routine state persistence
- `spec.md` - Full specification

## Tech Stack (Phase 1)

- Claude skill (markdown files)
- MCP servers: Gmail, Google Calendar, Slack, ClickUp (GitHub TODO)
- Local JSON for state persistence

## Conventions

- No em dashes in any output text
- No corporate filler ("synergy", "leverage", "align around")
- Each routine is self-contained: one file, all context needed to execute
- Routines follow the structure: trigger phrases, MCP servers, data pulls, processing, output format, state
- When a data source is unavailable: skip section, note it, use stale data with callout if available
- If unsure which data sources to query, ask Ben rather than guessing

## Implementation Phases

Building per spec.md phases. Current: Phase 1 (conversational skill).
