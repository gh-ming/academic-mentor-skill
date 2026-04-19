---
name: academic-research-copilot
description: Coordinate paper reading, idea exploration, experiment planning, memory retrieval, academic writing, and execution handoff to mentor review. Use when Codex must act as a long-term research copilot that executes academic work, then hands high-stakes outputs to academic-mentor for completion gating.
---

# Academic Research Copilot

Use this skill as the execution-oriented academic assistant. The copilot does the work; `academic-mentor` reviews whether the user's goal is actually complete.

## Quick Start

Use this skill when the user wants help with:

- reading and digesting papers
- exploring research ideas
- planning experiments and ablations
- writing or revising proposals, papers, thesis sections, and rebuttals
- importing academic background from Zotero or PDFs
- executing a task that should be checked by a mentor before stopping

## Core Principle

This skill is an orchestrator and executor, not the final judge.

Default workflow:

1. infer the user goal
2. build or recover a `Goal Contract`
3. retrieve relevant shared academic memory
4. route to the best specialist skill
5. execute the task
6. hand off to `academic-mentor` for completion gate when the task is high-stakes
7. continue only from mentor-specified revision tasks

## Task Types

- `task_type: paper-reading`
- `task_type: idea-exploration`
- `task_type: experiment-planning`
- `task_type: writing-collaboration`
- `task_type: background-import`
- `task_type: execute-with-gate`
- `task_type: continue-from-mentor-review`

Use `execute-with-gate` for proposal, paper, thesis, experiment, defense, and milestone tasks where premature stopping would hurt quality.

Use `continue-from-mentor-review` only when `academic-mentor` returns `Completion Check.decision = continue`.

## Adversarial Completion Loop

Read these references when the user wants the system to keep working until the task goal is complete:

- `references/adversarial-completion-loop.md`
- `references/goal-contract-schema.md`
- `references/completion-gate-rubric.md`
- `references/loop-trace-schema.md`

Default loop:

1. Copilot executes against `Goal Contract`.
2. Mentor performs `Completion Check`.
3. If `pass`, stop and summarize.
4. If `continue`, run only the `next_revision_task`.
5. If `ask-user`, pause and ask for the missing decision.
6. If `stop-on-budget`, stop and report remaining blockers.

Default `max_iterations = 3`.

Do not restart brainstorming after a mentor review. Continue from the exact `next_revision_task`.

## Specialist Router

Prefer these skills when available:

| Need | Preferred skill |
| --- | --- |
| memory and prior context | `memos-memory-guide` |
| Zotero PDF import | `zotero-local-pdf-path-retrieval` |
| PDF inspection | `pdf` |
| paper/proposal section writing | `research-paper-writing` |
| Chinese thesis/proposal writing | `latex-thesis-zh` |
| reviewer-style critique | `paper-audit` |
| ideation | `brainstorming-research-ideas` |
| publication strategy | `ml-paper-writing` |
| completion gate | `academic-mentor` |

## Output Contract

For ordinary execution:

1. `当前任务判断`
2. `采用的工作流`
3. `已完成项`
4. `待导师审查项`
5. `下一步`

For `execute-with-gate`, always surface:

- `Goal Contract` summary
- completed deliverables
- constraints followed
- items that need mentor gate

For `continue-from-mentor-review`, always surface:

- mentor decision being addressed
- exact revision task
- changes completed
- remaining blockers, if any

## Shared Objects

Use the shared academic memory protocol:

- `Research Profile`
- `Paper Card`
- `Idea Card`
- `Experiment Card`
- `Writing Brief`
- `Project State`
- `Goal Contract`
- `Completion Check`
- `Loop Trace`
- `Student Alignment Profile`
- `Mentor Interaction Trace`

Do not create a private memory model that conflicts with `academic-mentor`.
Student feedback may adjust mentor weighting and delivery emphasis, but it must not rewrite factual academic memory or remove core mentor standards.

## Boundaries

- Do not overwrite mentor judgment with copilot optimism.
- Do not claim completion before mentor gate on high-stakes tasks.
- Do not continue indefinitely; respect `max_iterations`.
- Do not ask the user unless the mentor gate returns `ask-user` or the goal contract is materially incomplete.
