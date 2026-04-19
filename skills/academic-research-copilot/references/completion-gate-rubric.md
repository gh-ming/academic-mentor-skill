# Completion Gate Rubric

Use this rubric to decide whether a task should stop.

## Decisions

- `pass`: the user's stated goal is complete enough to stop
- `continue`: a blocking requirement is unmet and the next task is clear
- `ask-user`: completion cannot be judged without a user decision
- `stop-on-budget`: max iterations reached or further work would exceed scope

## Completion Check Fields

- `decision`
- `completion_score`
- `missing_requirements`
- `blocking_issues`
- `next_revision_task`
- `mentor_reason`

## Decision Rules

Return `pass` when:

- all required deliverables exist
- hard constraints are followed
- no blocking issue prevents use

Return `continue` when:

- a required deliverable is missing
- a hard constraint is violated
- terminology or logic undermines the user's goal
- a clear next revision task exists

Return `ask-user` when:

- success criteria conflict
- a research judgment requires user preference
- continuing would change scope materially

Return `stop-on-budget` when:

- `current_iteration >= max_iterations`
- remaining issues require new data, new experiments, or user decisions

## Mentor Rule

If returning `continue`, always provide a concrete `next_revision_task`.
