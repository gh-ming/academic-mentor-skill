# Source Distillation and Testing

This document adapts the useful parts of `nuwa-skill` to an academic-mentor setting.

The key lesson from `nuwa-skill` is not "imitate a celebrity." The key lesson is:

- collect richer public evidence
- distill durable judgment rules
- distill expression DNA without collapsing into caricature
- validate the distilled persona on real tasks

For an academic mentor skill, this is more important than style.

In this repository, distillation feeds a unified mentor system with an internal advisor council rather than a pure single-persona prompt.

The current default council uses Fei-Fei Li, Kaiming He, and Mu Li as high-value academic inspirations, but the mechanism is intentionally extensible. If a public figure has enough stable, source-backed research material, the same pipeline can be used to turn that person into a new research-mentor source pack.

## 1. Distillation Goal

We are not extracting:

- speech quirks
- famous one-liners
- surface-level "vibe"

We are extracting:

- problem taste
- method taste
- evidence standards
- guidance style
- expression DNA
- narrative preferences
- anti-patterns
- honest boundaries

## 2. Source Types To Use

For each mentor inspiration, collect from four buckets:

1. papers and project pages
   - what problems they repeatedly choose
   - how they frame contribution boundaries
2. official profiles and institutional pages
   - how they describe their long-term agenda
3. talks, lectures, and course videos
   - how they teach, prioritize, and explain difficult questions
4. interviews
   - only when they reveal durable views on research, engineering, or judgment

Recommended rule:

- do not let interviews dominate the distillation
- papers and official materials should remain the primary anchors
- when source quality conflicts, trust the paper record for judgment rules and use videos mainly for delivery refinement

## 3. Distillation Layers

Inspired by `nuwa-skill`, but adapted for academic use:

### Layer 1: How they frame problems

- what counts as a worthy problem
- what scope is too broad or too trivial

### Layer 2: How they evaluate methods

- what kinds of methods they seem to respect
- when complexity is justified
- when simplicity is the real advance

### Layer 3: How they evaluate evidence

- what experiments appear necessary
- what kinds of claims require stronger support
- what gaps would likely trigger skepticism

### Layer 4: What they reject

- common anti-patterns
- overclaiming patterns
- method-over-problem patterns
- research-fashion chasing

### Layer 4.5: Paper DNA

- how papers define the central bottleneck
- how contribution boundaries are controlled
- how experiments are ordered to support the claim
- how limitations are acknowledged
- how the writing moves from significance to mechanism to validation

For academic mentors, this layer is often more important than talk-style imitation.

### Layer 5: Guidance style

- how they point out problems
- how they turn criticism into a learning route
- how they would likely help a student improve rather than only reject

### Layer 5.5: Expression DNA

- whether they lead with framing or conclusion
- how compressed or expansive their sentences tend to be
- how they ask hard questions
- how much warmth, distance, or didactic sequencing appears in public materials
- which style signals are stable enough to preserve without becoming parody

### Layer 6: Honest boundaries

- what cannot be reliably inferred from public sources
- where the skill should stay uncertain

## 4. Minimum Evidence Rule

Only promote a rule into a source pack when it satisfies at least two of the following:

- appears across multiple papers/projects
- is visible in both technical output and public explanation
- predicts how the person would likely react to a new but related academic problem

This is the academic analogue of `nuwa-skill`'s multi-source verification idea.

## 5. Recommended Test Types

The skill should not be considered good because it "sounds right." Test it on academic tasks.

### Test A: Publicly answerable historical problems

Use questions where the source person's actual public work gives strong hints about their likely judgment.

Examples:

- evaluate a method-heavy but problem-weak proposal
- critique a benchmark-driven paper with weak broader significance
- decide whether a direction is a real long-term thesis topic or only a paper idea

### Test B: Unseen but adjacent academic problems

Ask about a new academic question the source person did not literally answer publicly.

Good output:

- applies the distilled rules
- stays within reasonable uncertainty

Bad output:

- acts omniscient
- gives overconfident judgments with no clear basis

### Test C: Multi-turn academic stress tests

Run the skill across several turns:

- first question: broad problem framing
- second question: method critique
- third question: experiment plan
- fourth question: defense risk

The persona should remain stable and not drift into generic coaching.

### Test D: Council differentiation

Run the same case through:

- `Fei-Fei advisor`
- `Kaiming advisor`
- `Li-Mu advisor`
- unified mentor synthesis

Good output:

- real difference in emphasis
- no contradiction without explanation
- one final synthesis that preserves the valuable disagreement
- recognizable differences in cadence and framing, not only content

## 6. Academic Test Matrix

Use at least these scenario classes:

- `proposal validity`
- `direction triage`
- `paper logic review`
- `defense attack simulation`
- `milestone go/no-go`

For each class, evaluate:

- problem-first discipline
- method judgment quality
- evidence sensitivity
- resistance to hype
- clarity of next action
- quality of advisor differentiation
- quality of final synthesis

## 7. Recommendation For This Repo

Near-term priority:

1. enrich each source pack with more paper / project / lecture / video / interview anchors
2. make the source packs support advisor-specific signals, not just prose summaries
3. test both advisor differentiation and unified-mentor synthesis
4. add 5-10 canonical academic prompts and expected judgment criteria

That would make the repo much stronger than a packaging-only skill repo.

## 8. Generalized Mentor Distillation Workflow

To make this repo useful beyond the current three advisors, treat mentor creation as a reusable distillation workflow.

### Step 1: Choose a candidate

Pick a public figure only when there is enough durable material to support academic judgment extraction.

Good candidates usually have:

- a meaningful paper or project record
- clear public teaching or explanation artifacts
- repeated signs of stable problem taste and evidence standards

Weak candidates usually have:

- mostly motivational content
- only interviews and no serious technical output
- unstable or hype-driven public positions

### Step 2: Build a source inventory

For each candidate, collect:

1. representative papers and project pages
2. official homepage or institutional profile
3. public courses, lectures, keynotes, and technical videos
4. interviews only when they reveal durable research or guidance principles

This is where `nuwa-skill` is particularly useful as a reference: not because this repo wants to mimic celebrities, but because it shows how to do multi-source person distillation with more evidence and less guesswork.

### Step 3: Extract the academic layers

Do not jump from sources straight to persona copywriting. First extract:

- `problem worldview`
- `method worldview`
- `evidence worldview`
- `paper DNA`
- `guidance style`
- `expression DNA`
- `confidence and limits`

For academic mentors, `paper DNA` is usually the most important layer. A useful mentor is not just someone who sounds smart; it is someone whose paper logic can help another researcher define problems better, control claims better, and build better evidence chains.

### Step 4: Convert into a source pack

Every new mentor pack should use a stable structure, so it can be audited and later synthesized with other advisors.

Recommended sections:

- `source_inventory`
- `problem_worldview`
- `method_worldview`
- `evidence_worldview`
- `paper_dna`
- `guidance_style`
- `expression_dna`
- `derived_rules`
- `confidence_and_limits`

### Step 5: Test before promotion

Before a new mentor becomes part of the default library, test it on real academic tasks:

- proposal review
- direction triage
- paper logic review
- experiment plan review
- defense attack simulation

The pass criterion is not "sounds like the person." The pass criterion is whether the mentor stays stable, useful, and source-grounded across tasks.

### Step 6: Decide how it enters the system

A new mentor can enter in one of three ways:

- as a standalone optional source pack
- as a selectable advisor lens
- as part of the default unified mentor council

Not every source pack needs to become part of the default council. Some may be valuable only for special domains or special task types.
