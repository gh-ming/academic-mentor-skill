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
- If success criteria conflict, hand to mentor with `ask-user`.
- If `context_basis` is missing for a high-stakes academic task, run `Research Context Intake` before execution.
- Do not treat optional polish as a required success criterion.
- Preserve user-stated constraints over generic best practices.

## Minimal Example

```yaml
user_goal: revise the opening report abstract and experiment plan
success_criteria:
  - title, abstract, research questions, and experiments use consistent framing
  - terminology fits remote sensing context
  - third research problem is not a disconnected add-on
deliverables:
  - edited proposal sections
  - short completion summary
constraints:
  - preserve TSP-Former and G-TMoE roles
  - avoid inflated wording
context_basis:
  - existing Research Profile
  - user-provided opening report draft
context_confidence: medium
out_of_scope:
  - rebuild the whole thesis
max_iterations: 3
current_iteration: 1
```
