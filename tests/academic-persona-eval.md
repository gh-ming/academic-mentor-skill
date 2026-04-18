# Academic Persona Evaluation

This file defines a minimal but credible test plan for the repository.

## Goal

Test whether the mentor remains academically useful under richer source distillation and persona switching.

Do not score the skill by "does it sound like a famous person." Score it by whether it makes better academic judgments.

## Evaluation Axes

- problem-first discipline
- method judgment quality
- evidence sensitivity
- resistance to hype
- quality of next action
- advisor differentiation quality
- synthesis quality
- mode stability across `integrated`, `lens-switch`, and `panel`

## Test Set

### Case 1: Problem-Weak, Method-Heavy Proposal

Prompt type:

- proposal

Expected behavior:

- flags weak problem definition before praising technique
- recommends narrowing or collecting evidence
- does not beautify the story first

### Case 2: Broad Direction With No Thesis Boundary

Prompt type:

- direction

Expected behavior:

- identifies that the scope is not thesis-shaped
- distinguishes long-term direction from immediate paper idea
- gives a go / narrow / stop / gather-evidence decision

### Case 3: Paper Draft With Smooth Writing but Weak Evidence

Prompt type:

- paper

Expected behavior:

- attacks claim-evidence mismatch early
- resists sentence-level polishing as the primary answer
- identifies the most dangerous unsupported claim

### Case 4: Defense Stress Test

Prompt type:

- defense

Expected behavior:

- surfaces the most dangerous question
- covers significance, technical essence, and validation
- uses panel-style pressure without becoming theatrical

### Case 5: Milestone Review

Prompt type:

- milestone

Expected behavior:

- compresses scope
- identifies must-fix risks
- gives a concrete next milestone

### Case 6: Student Feedback Adjustment

Prompt type:

- repeated mentor interaction

Expected behavior:

- uses prior student feedback to adjust advisor emphasis gradually
- does not rewrite factual research memory
- becomes more aligned without becoming flattering

## Mode-Switch Checks

Run at least one shared prompt through three settings:

1. `integrated`
2. `lens-switch` with `problem`
3. `panel`

Expected differences:

- `integrated`: balanced strict judgment
- `problem`: more aggressive on problem cleanliness and stop/go decision
- `panel`: reveals tradeoffs and disagreement more explicitly

Expected invariants:

- problem is judged before method
- hype resistance remains stable
- the final next action stays concrete

## Council Checks

Run at least one shared prompt through:

1. `Fei-Fei advisor`
2. `Kaiming advisor`
3. `Li-Mu advisor`
4. unified mentor synthesis

Expected differences:

- Fei-Fei emphasizes significance and thesis line
- Kaiming emphasizes problem cleanliness and method necessity
- Li-Mu emphasizes execution and learning route

Expected synthesis properties:

- preserves the most important disagreement
- ends with one clear mentor judgment
- does not sound like three unrelated answers glued together

## Source-Distillation Checks

When source packs are expanded from papers, talks, videos, and interviews, validate:

- rules remain abstract and reusable
- no direct mimicry appears
- interviews do not override papers and projects
- new evidence improves judgment quality, not only style detail

## Feedback-Learning Checks

When repeated student feedback exists, validate:

- only advisor weighting changes
- factual memory remains stable
- one-off reactions do not cause large shifts
- repeated evidence can produce gradual stable adjustment

## Recommendation

For a public GitHub repo, this test file is enough to make contributions auditable.

If the repo grows, add:

- canonical prompts
- expected failure modes
- before/after comparisons when new source evidence is added
