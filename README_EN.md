# Academic Mentor Skill Repo

[中文](./README.md) | English

This repository packages `academic-mentor` as a publishable academic skill repository. It is not a generic coaching persona. It is a strict doctoral-level mentor skill for research direction triage, proposal review, paper-logic critique, defense preparation, and milestone decisions.

## Repository Goals

This repo does three things:

1. packages `academic-mentor` into a standalone skill repo that can be installed or pushed to GitHub directly
2. grounds the mentor in public-source-derived research judgment rules instead of superficial imitation
3. upgrades it into a unified mentor system with an internal three-advisor council and feedback-based weighting

## What Is Included

- installable skill:
  - `skills/academic-mentor/`
- repo-level methodology docs:
  - `docs/skill-review-and-architecture.md`
  - `docs/source-distillation-and-testing.md`
  - `docs/persona-interaction-and-switching.md`
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
```

If you use another agent framework, point it at `skills/academic-mentor/`.

## Repository Layout

```text
academic-mentor-skill-repo/
├── README.md
├── README_EN.md
├── .gitignore
├── docs/
│   ├── skill-review-and-architecture.md
│   ├── source-distillation-and-testing.md
│   └── persona-interaction-and-switching.md
├── examples/
│   └── mode-switch-prompts.md
├── tests/
│   └── academic-persona-eval.md
└── skills/
    └── academic-mentor/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── advisor-persona.md
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
            ├── phd-scenario-optimization.md
            ├── student-feedback-learning.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
```

## Push to GitHub

This repo has already been initialized and committed locally. To publish:

```bash
git remote add origin <your-repo-url>
git push -u origin main
```

## Current Recommendations

If you continue improving this repo, the best priority order is:

1. keep enriching the three advisor source packs with papers, project pages, talks, videos, and interviews
2. validate whether the unified-surface plus internal-council model remains stable
3. use the built-in tests to check advisor differentiation and synthesis quality
4. only then consider packaging `academic-research-copilot` as a sibling skill
