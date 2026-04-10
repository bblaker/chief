# AI Chief of Staff

Executive assistant skill + scheduler for Ben (Head of Technology, Aptive Environmental).

## Architecture

Two modes sharing the same routines and system prompt:
- **Conversational**: Claude skill triggered by chat. Routes to MCP servers based on intent.
- **Scheduled**: Lambda/Node cron runs routines, delivers via Slack DM.

Key directories:
- `routines/` - Markdown routine definitions (one per file)
- `scheduler/` - TypeScript runner, Slack delivery, config
- `state/` - SQL schema for persistence
- `system-prompt.md` - Base persona and org context
- `SKILL.md` - Skill entry point

## Tech Stack

- TypeScript (strict mode) for scheduler code
- Node 20+ runtime (Lambda target)
- Anthropic SDK (`@anthropic-ai/sdk`) for API calls
- MCP servers: Gmail, Google Calendar, Slack, ClickUp, GitHub (TBD)
- SQLite for local dev state persistence, DynamoDB for prod
- Slack Web API for delivery

## Build & Dev

```
npm run build        # tsc
npm run dev          # tsx scheduler/runner.ts
npm run lint         # eslint
npm run typecheck    # tsc --noEmit
npm test             # vitest
```

## Conventions

- No em dashes in any output text
- No corporate filler ("synergy", "leverage", "align around")
- Routine markdown files follow the structure in spec.md (triggers, schedule, MCP servers, data pulls, processing, output format)
- Each routine is self-contained: one file, all context needed to execute
- Scheduler config is YAML, routines are Markdown
- State persistence functions return typed interfaces, not `unknown`
- MCP server selection is driven by `ROUTINE_MCP_MAP` in runner.ts

## Testing

- Unit tests for: routine prompt building, state extraction, MCP routing logic
- Integration tests mock the Anthropic SDK response, verify Slack delivery format
- No tests needed for routine markdown content (those are prompts, not code)

## Implementation Phases

Building per spec.md phases. Current phase tracked in commit messages.
