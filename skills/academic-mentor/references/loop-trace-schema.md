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
- The trace should explain why the task continued or stopped.
- Do not use the trace as a place for long critique; put critique in `Completion Check`.
