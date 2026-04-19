# Academic Mentor Skill Repo

[中文](./README.md) | English

What if some of the world's strongest scientists could become your long-term research mentors, guiding your thesis, your research direction, and the way you learn to do science?

Not just answering questions. Not just giving you more papers to read. A real mentor should narrow a vague direction, challenge a method-heavy but problem-light idea, ask whether your evidence supports your claim, and expose the dangerous weaknesses before a proposal defense or thesis defense does.

This repo turns that idea into an installable skill system. One skill works with you as a research copilot: reading papers, organizing knowledge, planning experiments, and drafting academic writing. The other skill acts as a strict mentor: judging research direction, problem definition, evidence quality, and whether the task is truly complete. They are designed to disagree productively: the copilot executes, the mentor reviews, and the system continues when the user's goal has not been met.

This is not a generic coaching persona. It is an academic mentor-copilot repository. `academic-research-copilot` executes academic work, while `academic-mentor` reviews whether the user's goal is complete. Together they support research direction triage, proposal review, paper-logic critique, defense preparation, milestone decisions, and bounded continue-until-complete loops.

## Why This Exists

Most AI academic assistants do not fail because they lack knowledge. They fail because they lack mentor-level judgment:

- They can polish a sentence without noticing that the claim behind it is unsupported.
- They can list many methods without asking whether those methods serve a clean problem.
- They can encourage exploration without telling you when to narrow, gather evidence, or stop.
- They can draft a proposal that looks complete without checking whether the title, research questions, technical route, and experiments actually cohere.

This repo aims to turn an academic assistant into a research-training system: the copilot helps you do the work, and the mentor forces the work to become defensible.

## Repository Goals

This repo does four things:

1. packages `academic-mentor` and `academic-research-copilot` into a dual-skill repo that can be installed or pushed to GitHub directly
2. grounds the mentor in public-source-derived research judgment rules instead of superficial imitation
3. converts the mentor traits inspired by Fei-Fei Li, Kaiming He, and Mu Li into auditable, testable, internally weighted judgment mechanisms
4. upgrades the system into copilot execution plus mentor review, with bounded continuation and feedback-based weighting

## What Is Included

- installable skill:
  - `skills/academic-mentor/`
  - `skills/academic-research-copilot/`
- repo-level methodology docs:
  - `docs/skill-review-and-architecture.md`
  - `docs/source-distillation-and-testing.md`
  - `docs/persona-interaction-and-switching.md`
  - `docs/adversarial-completion-loop.md`
- examples and test design:
  - `examples/mode-switch-prompts.md`
  - `tests/academic-persona-eval.md`

## Core Logic

The skill's evaluation order is fixed:

1. judge whether the problem is worth doing
2. judge whether the method actually serves the problem
3. judge whether the evidence supports the claim
4. only then consider wording and presentation

Its default product shape is now a unified mentor system:

- the user sees one continuous mentor
- internally the system runs three advisors
- student feedback adjusts advisor weighting instead of rewriting factual memory

The internal advisors are:

- `Fei-Fei advisor`
  - significance, larger scientific framing, narrative coherence
- `Kaiming advisor`
  - clean problem definition, method necessity, research taste
- `Li-Mu advisor`
  - decomposition, validation path, executable next steps

These are internal judgment analyzers, not role-play personas.

## Source Distillation

The repo already includes three source packs:

- `fei-fei-li-source-pack.md`
- `kaiming-he-source-pack.md`
- `li-mu-source-pack.md`

To raise quality further, the skill should be distilled from richer source types:

- representative papers and project pages
- official homepages and institutional materials
- high-signal public lectures, talks, and videos
- interviews that reveal durable research values

The most important upgrade is not speech imitation but paper-expression distillation:

- how papers define the real problem
- how papers control contribution boundaries
- how papers organize evidence and experiments
- how papers handle limitations and avoid overclaim

This layer is now explicit in the skill:

- `references/paper-first-distillation.md`
- `references/research/fei-fei-li-paper-dna.md`
- `references/research/kaiming-he-paper-dna.md`
- `references/research/li-mu-paper-dna.md`

It is now further refined into three representative paper-profile cards:

- `references/research/fei-fei-li-paper-profile-card.md`
- `references/research/kaiming-he-paper-profile-card.md`
- `references/research/li-mu-paper-profile-card.md`

and three representative paper-anchor notes:

- `references/research/fei-fei-li-representative-paper-anchors.md`
- `references/research/kaiming-he-representative-paper-anchors.md`
- `references/research/li-mu-representative-paper-anchors.md`

See:

- [docs/source-distillation-and-testing.md](./docs/source-distillation-and-testing.md)
- [examples/mode-switch-prompts.md](./examples/mode-switch-prompts.md)
- [tests/academic-persona-eval.md](./tests/academic-persona-eval.md)

## Academic Focus

The goal is not to make famous people "talk." The goal is to improve academic judgment quality in scenarios such as:

- whether a proposal topic is valid
- whether a direction is worth continuing
- whether a paper is solving a real problem
- whether the method is larger than the problem
- where a defense is most vulnerable

The paper pathway is now split into two submodes:

- `paper-logic`
  - judge whether the paper is really solving a real problem and whether the argument stands
- `paper-strategy`
  - if the direction is broadly valid, decide what to revise next, what evidence to add, and what to cut or weaken

## Adversarial Completion Hook

The repo now includes a skill-level completion-check protocol:

- `academic-research-copilot` executes the task
- `academic-mentor` judges whether the goal is complete
- if mentor returns `continue`, copilot executes only the next mentor-specified revision task
- default maximum loop count is 3

Core objects:

- `Goal Contract`
- `Completion Check`
- `Loop Trace`

This is client-independent in v1. Future adapters can map it to Claude Code Stop hooks or an external harness.

## Persona Interaction and Switching

This is one of the most important next-stage enhancements.

Recommended layers:

- `integrated`
  - default, one unified mentor voice with internal multi-advisor reasoning
- `lens-switch`
  - explicit emphasis on one advisor when the user wants one dominant viewpoint
- `panel/debate`
  - the three advisors review the same question, then synthesize a final judgment

See:

- [docs/persona-interaction-and-switching.md](./docs/persona-interaction-and-switching.md)

## Installation

Copy the skill into your local skills directory:

```bash
cp -R skills/academic-mentor ~/.codex/skills/
cp -R skills/academic-research-copilot ~/.codex/skills/
```

If you use another agent framework, point it at `skills/academic-mentor/` and `skills/academic-research-copilot/`.

## Repository Layout

```text
academic-mentor-skill-repo/
├── README.md
├── README_EN.md
├── .gitignore
├── docs/
│   ├── skill-review-and-architecture.md
│   ├── source-distillation-and-testing.md
│   ├── persona-interaction-and-switching.md
│   └── adversarial-completion-loop.md
├── examples/
│   └── mode-switch-prompts.md
├── tests/
│   └── academic-persona-eval.md
└── skills/
    ├── academic-mentor/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── advisor-persona.md
            ├── advisor-expression-rules.md
            ├── mentor-council.md
            ├── source-grounding.md
            ├── fei-fei-li-source-pack.md
            ├── kaiming-he-source-pack.md
            ├── li-mu-source-pack.md
            ├── proposal-review-rubric.md
            ├── research-direction-triage.md
            ├── paper-guidance-rubric.md
            ├── defense-prep-rubric.md
            ├── milestone-review-rubric.md
            ├── adversarial-completion-loop.md
            ├── goal-contract-schema.md
            ├── completion-gate-rubric.md
            ├── loop-trace-schema.md
            ├── phd-scenario-optimization.md
            ├── student-feedback-learning.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
    └── academic-research-copilot/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── copilot-orchestration.md
            ├── adversarial-completion-loop.md
            ├── goal-contract-schema.md
            ├── completion-gate-rubric.md
            ├── loop-trace-schema.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
```

The research evidence layer now also includes video distillation notes:

- `references/research/video-source-map.md`
- `references/research/fei-fei-li-video-card.md`
- `references/research/kaiming-he-video-card.md`
- `references/research/li-mu-video-card.md`

It now also includes paper-DNA distillation notes:

- `references/paper-first-distillation.md`
- `references/research/fei-fei-li-paper-dna.md`
- `references/research/kaiming-he-paper-dna.md`
- `references/research/li-mu-paper-dna.md`
- `references/research/fei-fei-li-paper-profile-card.md`
- `references/research/kaiming-he-paper-profile-card.md`
- `references/research/li-mu-paper-profile-card.md`
- `references/research/fei-fei-li-representative-paper-anchors.md`
- `references/research/kaiming-he-representative-paper-anchors.md`
- `references/research/li-mu-representative-paper-anchors.md`

## Push to GitHub

This repo has already been initialized locally. After reviewing and committing the current changes, publish with:

```bash
git status
git add README.md README_EN.md docs examples tests skills
git commit -m "Add adversarial academic mentor-copilot skills"
git remote add origin <your-repo-url>
git push -u origin main
```

## Current Recommendations

If you continue improving this repo, the best priority order is:

1. keep enriching the three advisor source packs with papers, project pages, talks, videos, and interviews
2. prioritize paper-derived judgment rules over interview-style tone refinement
3. validate whether the unified-surface plus internal-council model remains stable
4. use the built-in tests to check advisor differentiation and synthesis quality
5. add an optional client-specific Stop hook or standalone harness only after the protocol is stable
