# Shared Memory Schema

Use this schema in both `academic-research-copilot` and `academic-mentor`.

## Objects

- `Research Profile`
- `Paper Card`
- `Idea Card`
- `Experiment Card`
- `Writing Brief`
- `Project State`
- `Research Context Brief`
- `Goal Contract`
- `Completion Check`
- `Loop Trace`
- `Student Alignment Profile`
- `Mentor Interaction Trace`

## Academic Objects

`Research Profile`: research topics, methods, datasets, writing preferences, terminology norms, current research line, source basis, confidence.

`Paper Card`: title, topic, problem, method, evidence, limitation, relation to user, status.

`Idea Card`: idea name, hypothesis, why it matters, main risk, minimal test, mentor status.

`Experiment Card`: goal, priority, dependency, pass condition, result summary.

`Writing Brief`: target document, target section, message, required evidence, naming constraints.

`Project State`: main problem, active subproblems, current stage, open risks, next decisions.

`Research Context Brief`: research direction, domain, core problem, known methods, known datasets, key constraints, representative sources, missing context, confidence.

## Loop Objects

`Goal Contract`: user goal, success criteria, deliverables, constraints, out of scope, max iterations, current iteration.

`Completion Check`: decision, completion score, missing requirements, blocking issues, next revision task, mentor reason.

`Loop Trace`: iteration, copilot action, mentor decision, changes required, status.

## Alignment Objects

`Student Alignment Profile`: preferred guidance intensity, common failure patterns, accepted feedback patterns, resisted feedback patterns, learning stage by topic, mentor weight adjustments.

`Mentor Interaction Trace`: task type, mentor internal weights, student response, advice adoption result, should adjust weights.

Alignment memory changes how advice is prioritized and delivered. It must not rewrite source-grounded academic facts, paper cards, experiment results, or mentor core rules.
