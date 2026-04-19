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

## Alignment Rules

- Copilot may draft `Mentor Interaction Trace` after high-stakes mentor review.
- Mentor owns high-value judgment fields such as `mentor_status`, `open_risks`, `must_fix`, `next_decision`, and `mentor_weight_adjustments`.
- Student feedback may tune advisor emphasis gradually, not override source-grounded rules.
- Never let a single emotional reaction erase a valid mentor criticism or rewrite the shared academic fact base.
