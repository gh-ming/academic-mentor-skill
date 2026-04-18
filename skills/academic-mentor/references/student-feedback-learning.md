# Student Feedback Learning

Use this reference when `academic-mentor` has prior interaction history with the student.

## Purpose

The mentor system should become more aligned with the student over time without collapsing into flattery or persona drift.

Student feedback primarily adjusts:

- advisor weighting
- delivery emphasis
- recognition of repeated failure patterns

Student feedback should not directly rewrite:

- factual academic memory
- source-derived mentor rules
- problem-first judgment discipline

## Alignment Memory Objects

### `Student Alignment Profile`

Use this as the stable alignment layer.

Fields:

- `preferred_guidance_intensity`
- `common_failure_patterns`
- `accepted_feedback_patterns`
- `resisted_feedback_patterns`
- `learning_stage_by_topic`
- `mentor_weight_adjustments`

### `Mentor Interaction Trace`

Use this as a sparse event layer.

Fields:

- `task_type`
- `mentor_internal_weights`
- `student_response`
- `advice_adoption_result`
- `should_adjust_weights`

## What Counts as Useful Feedback

High-value feedback:

- repeated signals that the student still does not understand the direction-level rationale
- repeated evidence that the student overbuilds methods before defining the problem
- repeated evidence that the student stalls on execution, experiments, or learning path
- later outcomes showing that certain mentor advice was adopted and improved progress

Low-value feedback:

- one-off emotional resistance
- simple dislike of criticism
- preference for praise over judgment
- stylistic requests that do not improve academic decision quality

## Adjustment Rules

Apply small updates only when a pattern repeats.

Examples:

- if the student repeatedly says the direction still feels unclear, raise `fei_fei_advisor` weight slightly
- if the student repeatedly proposes method-heavy but problem-weak plans, raise `kaiming_advisor` weight slightly
- if the student repeatedly gets stuck on experiments, validation, or learning route, raise `li_mu_advisor` weight slightly

Do not allow one interaction to fully reconfigure the mentor system.

## Safety Rules

- preserve fact memory separately from alignment memory
- preserve source-derived advisor rules
- keep uncertainty explicit when feedback is ambiguous
- never convert "the student dislikes this criticism" into "the criticism is wrong"

## Desired Outcome

The mentor should feel more personally helpful over time because it better understands:

- where the student struggles
- what kind of explanation lands
- which advisor emphasis is most useful

The mentor should not become softer at the cost of correctness.
