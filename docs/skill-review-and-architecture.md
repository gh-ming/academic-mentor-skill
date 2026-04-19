# Skill Review and Architecture

## Review Summary

`academic-mentor` is already strong as a judgment-oriented academic skill. Its main strengths are:

- a clear decision-first posture
- compact but stable task routing
- explicit persona grounding rules
- separation between persona rules, task rubrics, and memory references

The latest redesign pushes it beyond a packaged persona prompt into a mentor system:

- one unified mentor surface
- one internal three-advisor council
- one shared academic fact base
- one alignment layer for gradual feedback-based weighting

## Core Design Logic

### 1. Mentor-System Layer

The skill now uses one unified mentor surface, not multiple role-played voices.

Internally it runs a fixed advisor council:

- `Fei-Fei advisor`
  - significance
  - research narrative
  - broader scientific framing
- `Kaiming advisor`
  - clean problem definition
  - method necessity
  - research taste
- `Li-Mu advisor`
  - decomposition
  - execution clarity
  - validation path

These are implemented as judgment analyzers, not as mimicry.

### 2. Task Routing Layer

The skill routes into five high-level decision contexts:

- `proposal`
- `direction`
- `paper`
- `defense`
- `milestone`

Each route has a paired reference file to keep `SKILL.md` concise while preserving task-specific guidance.

### 2.5. Interaction-Mode Layer

The next meaningful extension is explicit persona-mode control:

- `integrated`
- `lens-switch`
- `panel`

This adds controllability without degrading the core design into role-play. In academic use, mode switching should change judgment emphasis, not voice imitation.

### 3. Synthesis Layer

The most important product change is synthesis.

The internal advisors may disagree, but the default user experience should still be one continuous mentor answer. The system therefore needs:

- advisor signals
- synthesis rules
- explicit weighting by task
- guardrails against turning disagreement into performance

### 4. Judgment Order

The skill's most important invariant is its evaluation order:

1. Is the problem worth doing?
2. Does the method actually serve that problem?
3. Does the evidence support the claim?
4. Only then consider wording or presentation.

This order prevents the mentor from becoming a writing polisher or a generic brainstorming partner.

### 5. Source Grounding Layer

The skill's persona is grounded through:

- `source-grounding.md`
- `fei-fei-li-source-pack.md`
- `kaiming-he-source-pack.md`
- `li-mu-source-pack.md`

The source packs make the grounding auditable and extensible. They are especially useful because the advisor council must be backed by more than prose description.

### 6. Memory Layer

The skill is designed to consume both shared academic memory and student-alignment memory instead of inventing context each time.

Key shared objects:

- `Research Profile`
- `Project State`
- `Paper Card`
- `Idea Card`
- `Experiment Card`
- `Writing Brief`
- `Student Alignment Profile`
- `Mentor Interaction Trace`

The mentor is intentionally read-heavy and write-light:

- it reads broad context before making judgments
- it only writes high-value judgment and alignment fields such as `mentor_status`, `open_risks`, `must_fix`, `next_decision`, and gradual weight adjustments

## Why the Structure Works

This structure keeps the skill stable under real academic use:

- persona drift is reduced because grounding is explicit
- judgment drift is reduced because routing and evaluation order are explicit
- context drift is reduced because shared-memory and alignment-memory references are explicit

It also makes the skill easier to publish:

- the installable artifacts are `skills/academic-mentor/` and `skills/academic-research-copilot/`
- the repo-level docs explain the architecture without polluting the skill folder itself

## Adversarial Completion Layer

The repo now packages the mentor and copilot as a dual-skill system:

- `academic-research-copilot` executes academic tasks against a `Goal Contract`
- `academic-mentor` reviews completion through a `Completion Check`
- failed checks return a concrete `Revision Task`
- `Loop Trace` records each round of execution, review, and continuation

This is a protocol-level hook rather than a client-specific integration. The first implementation keeps the loop bounded by default with `max_iterations = 3`, so the system can continue when the user's goal is not complete without turning into an infinite agent run.

The key invariant is role separation:

- the copilot is responsible for doing the work
- the mentor is responsible for judging whether the user's goal is complete
- the mentor can request another round, but the copilot must only execute the requested revision task
- after the budget is exhausted, the mentor must return `stop-on-budget` with remaining blockers

## Future Extension Points

- add more source packs for additional mentor inspirations
- strengthen source packs with paper / project / video / interview evidence rather than lightweight summaries
- add a small examples and test suite for mode stability
- add canonical feedback-learning examples once enough real mentoring traces exist
- split `paper` into `paper-logic` and `paper-strategy` if usage diverges
- add examples or tests outside the skill folder if you want a contributor workflow
- add a Claude Code Stop Hook adapter that maps `Completion Check.decision = continue` to a blocked stop event
- add a standalone loop harness for copilot -> mentor -> copilot execution when a client does not provide native hooks
