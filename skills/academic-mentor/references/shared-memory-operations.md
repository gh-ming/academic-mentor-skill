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

Default behavior:

- retrieve before judgment
- do not create broad knowledge inventories
- update shared memory only when the judgment materially affects future decisions
- treat `Research Profile` as a read-mostly background object unless a high-confidence judgment materially reframes it

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

## Conflict Rules

- shared memory is the single fact base across both skills
- if a new result conflicts with existing memory, refine or update rather than duplicating
- if certainty is low, keep uncertainty explicit instead of overwriting earlier conclusions
