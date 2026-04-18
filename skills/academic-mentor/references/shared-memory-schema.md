# Shared Memory Schema

Use this schema in both `academic-mentor` and `academic-research-copilot`. This is the shared academic memory bottom layer.

## Principles

- one shared fact base
- structured objects over vague summaries
- durable academic content only
- no silent duplication across skills

## Objects

### `Research Profile`

- `research_topics`
- `recurring_methods`
- `recurring_datasets`
- `writing_preferences`
- `terminology_norms`
- `current_research_line`
- `source_basis`
- `confidence`

Use for imported academic background that should shape future mentor judgments.

### `Paper Card`

- `title`
- `topic`
- `problem`
- `method`
- `evidence`
- `limitation`
- `relation_to_user`
- `status`: `reading | absorbed | revisit`

Use for papers, reports, tutorials, or survey items that materially affect the user's research.

### `Idea Card`

- `idea_name`
- `hypothesis`
- `why_it_might_matter`
- `main_risk`
- `minimal_test`
- `mentor_status`: `continue | narrow | stop | gather-evidence`

Use for ideas worth revisiting, not for every passing brainstorm.

### `Experiment Card`

- `goal`
- `priority`
- `dependency`
- `pass_condition`
- `result_summary`

Use for experiments that change research decisions or document the route to evidence.

### `Writing Brief`

- `target_document`
- `target_section`
- `message`
- `required_evidence`
- `naming_constraints`

Use for paper sections, proposal sections, thesis writing, review responses, and similar writing tasks.

### `Project State`

- `main_problem`
- `active_subproblems`
- `current_stage`
- `open_risks`
- `next_decisions`

Use as the high-level snapshot for the user's active research line.

### `Student Alignment Profile`

- `preferred_guidance_intensity`
- `common_failure_patterns`
- `accepted_feedback_patterns`
- `resisted_feedback_patterns`
- `learning_stage_by_topic`
- `mentor_weight_adjustments`

Use for durable mentor-student alignment information. This object stores how the student tends to receive guidance and where the mentor system should shift emphasis over time.

### `Mentor Interaction Trace`

- `task_type`
- `mentor_internal_weights`
- `student_response`
- `advice_adoption_result`
- `should_adjust_weights`

Use for repeated mentoring threads where the system needs a sparse trace of whether advice was accepted, resisted, or validated later.

## Mentor Fields

These fields are primarily written by `academic-mentor`:

- `mentor_status`
- `open_risks`
- `must_fix`
- `next_decision`
- `mentor_weight_adjustments`
- `advice_adoption_result`

These fields should remain sparse and high-value.
