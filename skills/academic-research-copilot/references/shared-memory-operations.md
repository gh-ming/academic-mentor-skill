# Shared Memory Operations

Use these operations across `academic-research-copilot` and `academic-mentor`.

## Operations

- `retrieve`: read relevant shared objects before acting
- `draft`: create a proposed object from current work
- `refine`: update an object with better evidence or wording
- `promote_to_shared`: treat an object as durable memory
- `update_status`: change status fields after mentor review or task completion

## Loop Rules

- Copilot drafts `Goal Contract` and `Loop Trace`.
- Mentor writes `Completion Check`.
- Copilot updates `Loop Trace` after acting on mentor review.
- Do not promote temporary brainstorming into shared memory unless it affects future work.
