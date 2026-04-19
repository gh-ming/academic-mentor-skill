# Loop Trace Schema

Use `Loop Trace` to preserve continuity across copilot execution and mentor review.

## Fields

- `iteration`
- `copilot_action`
- `mentor_decision`
- `changes_required`
- `status`

## Status Values

- `executed`
- `passed`
- `continued`
- `waiting-for-user`
- `stopped-on-budget`

## Rules

- Record only high-value loop events.
- Do not turn every small edit into a trace item.
- The trace should explain why the task continued or stopped.
