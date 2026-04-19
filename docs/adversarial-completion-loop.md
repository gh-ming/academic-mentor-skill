# Adversarial Completion Loop

This document explains the repo-level loop protocol shared by `academic-research-copilot` and `academic-mentor`.

The goal is not to make the agent run forever. The goal is to prevent premature stopping on high-stakes academic work when the user goal is not actually complete.

## Roles

`academic-research-copilot` is the executor.

It should:

- infer or recover the `Goal Contract`
- execute the requested academic task
- record completed deliverables and constraints followed
- hand off high-stakes outputs to `academic-mentor`
- continue only from the mentor's explicit `next_revision_task`

`academic-mentor` is the completion gate.

It should:

- judge whether the user's stated goal is complete
- distinguish missing requirements from optional quality improvements
- return `pass`, `continue`, `ask-user`, or `stop-on-budget`
- produce a concrete next revision task when the decision is `continue`
- avoid doing large execution work that belongs to the copilot

## Loop Contract

Each loop starts from a `Goal Contract`:

- `user_goal`
- `success_criteria`
- `deliverables`
- `constraints`
- `context_basis`
- `context_confidence`
- `out_of_scope`
- `max_iterations`
- `current_iteration`

Each mentor gate produces a `Completion Check`:

- `decision`
- `completion_score`
- `missing_requirements`
- `blocking_issues`
- `next_revision_task`
- `mentor_reason`

Each iteration appends a `Loop Trace`:

- `iteration`
- `copilot_action`
- `mentor_decision`
- `changes_required`
- `status`

Before building the `Goal Contract`, high-stakes academic tasks should run research context intake from shared memory, Zotero, PDFs, user-provided files, or the user's stated direction. The resulting context basis must be visible to the mentor gate.

The canonical schemas live inside each skill's `references/` directory so both skills use the same object definitions.

## Decision Semantics

`pass` means the user goal has been met. The output can still be imperfect, but no blocking requirement remains.

`continue` means at least one blocking requirement remains and can be addressed without asking the user. The mentor must provide one concrete `next_revision_task`.

`ask-user` means continuing would require a user decision because the goal is ambiguous, success criteria conflict, or a research choice cannot be safely inferred.

`stop-on-budget` means the loop has reached `max_iterations`. The system must stop, list remaining blockers, and ask the user whether to continue with a new goal contract.

## Bounded Strategy

Default `max_iterations = 3`.

Iteration 1 may include full execution and mentor review.

Iterations 2-3 must only address blocking issues named by the mentor. They must not reopen brainstorming, expand scope, or rewrite the task objective.

If the third iteration still fails, the mentor returns `stop-on-budget`.

## Future Adapters

This repo currently implements a skill-level protocol, not a runtime hook.

A future Claude Code Stop hook adapter can map:

- `Completion Check.decision = pass` to allow stop
- `Completion Check.decision = continue` to block stop and inject `next_revision_task`
- `Completion Check.decision = ask-user` to stop and request input
- `Completion Check.decision = stop-on-budget` to allow stop with blockers

A future standalone harness can run:

1. copilot execution
2. mentor completion gate
3. copilot revision task
4. repeated gate until pass or budget exhaustion
