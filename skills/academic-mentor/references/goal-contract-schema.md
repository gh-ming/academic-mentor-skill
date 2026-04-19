# Goal Contract Schema

Use `Goal Contract` to make completion checkable.

## Fields

- `user_goal`: the user's actual task objective
- `success_criteria`: observable conditions that mean the task is complete
- `deliverables`: concrete outputs expected by the user
- `constraints`: hard requirements, terminology, file paths, style, or scope rules
- `context_basis`: Zotero/PDF/shared-memory/user-stated direction used to ground the task
- `context_confidence`: `high | medium | low`
- `out_of_scope`: work that should not be done in this loop
- `max_iterations`: default `3`
- `current_iteration`: starts at `1`

## Rules

- If success criteria are missing, infer reasonable criteria from the user's prompt and context.
- If success criteria conflict, return `Completion Check.decision = ask-user`.
- If `context_basis` is missing for a high-stakes academic task, return `continue` or `ask-user` instead of `pass`.
- Do not treat optional polish as a required success criterion.
- Preserve user-stated constraints over generic best practices.
