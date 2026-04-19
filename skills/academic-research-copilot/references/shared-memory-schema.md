# Shared Memory Schema

Use this schema in both `academic-research-copilot` and `academic-mentor`.

## Objects

- `Research Profile`
- `Paper Card`
- `Idea Card`
- `Experiment Card`
- `Writing Brief`
- `Project State`
- `Goal Contract`
- `Completion Check`
- `Loop Trace`

## Academic Objects

`Research Profile`: research topics, methods, datasets, writing preferences, terminology norms, current research line, source basis, confidence.

`Paper Card`: title, topic, problem, method, evidence, limitation, relation to user, status.

`Idea Card`: idea name, hypothesis, why it matters, main risk, minimal test, mentor status.

`Experiment Card`: goal, priority, dependency, pass condition, result summary.

`Writing Brief`: target document, target section, message, required evidence, naming constraints.

`Project State`: main problem, active subproblems, current stage, open risks, next decisions.

## Loop Objects

`Goal Contract`: user goal, success criteria, deliverables, constraints, out of scope, max iterations, current iteration.

`Completion Check`: decision, completion score, missing requirements, blocking issues, next revision task, mentor reason.

`Loop Trace`: iteration, copilot action, mentor decision, changes required, status.
