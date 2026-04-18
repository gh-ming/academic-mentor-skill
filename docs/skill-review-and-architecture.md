# Skill Review and Architecture

## Review Summary

`academic-mentor` is already strong as a judgment-oriented academic skill. Its main strengths are:

- a clear decision-first posture
- compact but stable task routing
- explicit persona grounding rules
- separation between persona rules, task rubrics, and memory references

The main cleanup required for packaging was structural rather than conceptual:

- remove a duplicated `shared_memory_object` interface line
- package the skill into a standalone repository
- explain the internal logic at the repo level so future contributors can modify it safely

## Core Design Logic

### 1. Persona Layer

The skill uses one unified mentor voice, not multiple role-played voices.

It combines three derived lenses:

- `Fei-Fei lens`
  - significance
  - research narrative
  - broader scientific framing
- `Kaiming lens`
  - clean problem definition
  - method necessity
  - research taste
- `Muyu lens`
  - decomposition
  - execution clarity
  - validation path

These are implemented as judgment rules, not as mimicry.

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

### 3. Judgment Order

The skill's most important invariant is its evaluation order:

1. Is the problem worth doing?
2. Does the method actually serve that problem?
3. Does the evidence support the claim?
4. Only then consider wording or presentation.

This order prevents the mentor from becoming a writing polisher or a generic brainstorming partner.

### 4. Source Grounding Layer

The skill's persona is grounded through:

- `source-grounding.md`
- `fei-fei-li-source-pack.md`
- `kaiming-he-source-pack.md`
- `li-mu-source-pack.md`

The source packs make the grounding auditable and extensible. They are especially useful if the persona needs later refinement or if additional mentors are added.

### 5. Memory Layer

The skill is designed to consume a shared academic memory schema instead of inventing context each time.

Key shared objects:

- `Research Profile`
- `Project State`
- `Paper Card`
- `Idea Card`
- `Experiment Card`
- `Writing Brief`

The mentor is intentionally read-heavy and write-light:

- it reads broad context before making judgments
- it only writes high-value judgment fields such as `mentor_status`, `open_risks`, `must_fix`, and `next_decision`

## Why the Structure Works

This structure keeps the skill stable under real academic use:

- persona drift is reduced because grounding is explicit
- judgment drift is reduced because routing and evaluation order are explicit
- context drift is reduced because shared-memory references are explicit

It also makes the skill easier to publish:

- the installable artifact is just `skills/academic-mentor/`
- the repo-level docs explain the architecture without polluting the skill folder itself

## Future Extension Points

- add more source packs for additional mentor inspirations
- strengthen source packs with paper / project / video / interview evidence rather than lightweight summaries
- add a small examples and test suite for mode stability
- split `paper` into `paper-logic` and `paper-strategy` if usage diverges
- add examples or tests outside the skill folder if you want a contributor workflow
- package `academic-research-copilot` as a sibling repo or mono-repo later
