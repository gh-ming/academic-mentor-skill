# Adversarial Completion Loop

Use this protocol when the user wants the assistant to keep working until the task goal is complete.

## Roles

- `academic-research-copilot`: executor
- `academic-mentor`: completion gate and adversarial reviewer

The copilot performs the work. The mentor decides whether the user's stated goal has been met.

## Loop

1. Build or retrieve research context from shared memory, Zotero, PDFs, files, or the user's stated direction.
2. Build a `Goal Contract` with `context_basis` and `context_confidence`.
3. Copilot executes the requested work.
4. Mentor reviews against the `Goal Contract` and context basis.
5. Mentor returns one `Completion Check`.
6. If `pass`, the loop stops.
7. If `continue`, copilot executes only `next_revision_task`.
8. If `ask-user`, pause for user input.
9. If `stop-on-budget`, stop and report remaining blockers.

## Defaults

- `max_iterations = 3`
- high-stakes academic tasks require `context_basis`
- do not broaden scope after iteration 1
- do not optimize for perfection; optimize for the user's stated goal
- do not loop on optional improvements

## High-Stakes Tasks

Always use the loop for:

- PhD proposal/opening report revisions
- paper logic or submission readiness
- experiment plans
- defense preparation
- milestone go/no-go decisions

## Non-Goals

This is a skill-level protocol, not a client-specific hook implementation.

Future adapters may map `Completion Check.decision = continue` to a Claude Code Stop hook or an external harness, but v1 remains client-independent.
