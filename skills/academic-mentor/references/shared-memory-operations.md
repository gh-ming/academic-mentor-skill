# Shared Memory Operations

Use this operation model in both skills.

## Operations

- `retrieve`: read the relevant shared objects before continuing
- `draft`: create an initial object when a task produces durable academic knowledge
- `refine`: improve an existing object with stronger evidence or clearer wording
- `promote_to_shared`: elevate an object only when it is durable enough for long-term reuse
- `update_status`: modify high-value fields after new evidence or mentor judgment

## Ownership

### `academic-research-copilot`

Primary writer for:

- `Paper Card`
- initial `Idea Card`
- initial `Experiment Card`
- `Writing Brief`
- `Project State` updates

Default behavior:

- retrieve first
- draft/refine after the task
- promote to shared only when the output is likely to matter again

### `academic-mentor`

Primary updater for:

- `mentor_status`
- `open_risks`
- `must_fix`
- `next_decision`
- `Student Alignment Profile`
- `Mentor Interaction Trace`

Default behavior:

- retrieve before judgment
- do not create broad knowledge inventories
- update shared memory only when the judgment materially affects future decisions
- treat `Research Profile` as a read-mostly background object unless a high-confidence judgment materially reframes it
- treat `Student Alignment Profile` as gradual alignment memory, not as a place to overwrite mentor principles
- write `Mentor Interaction Trace` sparsely after high-value mentor turns or when later outcomes validate or invalidate advice

## Promotion Rules

Promote to shared memory when the item is:

- reusable in future research decisions
- stable enough to survive beyond the current chat turn
- specific enough to guide writing, experiments, or direction choices

Do not promote:

- casual chat
- low-confidence speculation
- temporary wording choices with no long-term consequence
- brainstorm fragments that were not evaluated
- one-off emotional reactions that have not repeated

## Conflict Rules

- shared memory is the single fact base across both skills
- fact memory and alignment memory must remain logically separated
- if a new result conflicts with existing memory, refine or update rather than duplicating
- if certainty is low, keep uncertainty explicit instead of overwriting earlier conclusions
- student preference can adjust advisor weighting, but cannot directly rewrite factual research memory

## Completion Loop Rules

- `academic-research-copilot` drafts `Goal Contract` and executes against it.
- `academic-mentor` writes `Completion Check`.
- `academic-research-copilot` updates `Loop Trace` after acting on mentor review.
- If `Completion Check.decision = continue`, the next copilot task must be the mentor's `next_revision_task`.
- If `Completion Check.decision = stop-on-budget`, neither skill should continue the loop without user confirmation.
