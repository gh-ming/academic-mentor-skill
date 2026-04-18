# Academic Mentor Skill Repo

This repository packages `academic-mentor` as a publishable Codex/Claude-style skill repository. The skill is designed as a strict doctoral-level academic mentor for research direction judgment, proposal review, paper logic review, defense preparation, and milestone triage.

## What This Repo Contains

- A directly installable skill folder at `skills/academic-mentor/`
- A reviewed and cleaned `SKILL.md`
- Persona grounding packs for Fei-Fei Li, Kaiming He, and Li Mu
- Shared academic-memory schema references
- Repository-level documentation explaining the skill's logic and structure

## Repository Layout

```text
academic-mentor-skill-repo/
├── README.md
├── .gitignore
├── docs/
│   └── skill-review-and-architecture.md
└── skills/
    └── academic-mentor/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── advisor-persona.md
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
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
```

## Skill Logic

The skill is built around four layers:

1. Persona layer
   - one integrated mentor voice
   - grounded in public academic sources, not imitation
2. Task-routing layer
   - `proposal`, `direction`, `paper`, `defense`, `milestone`
3. Judgment layer
   - problem first
   - method second
   - evidence third
   - wording last
4. Shared-memory layer
   - reads `Research Profile`, `Project State`, `Paper Card`, `Idea Card`, `Experiment Card`, and `Writing Brief`

## Installation

Copy the skill folder into your skills directory:

```bash
cp -R skills/academic-mentor ~/.codex/skills/
```

If you use another agent framework, point that framework at the `skills/academic-mentor/` directory.

## Recommended Publishing Flow

Initialize a remote and push:

```bash
git remote add origin <your-repo-url>
git push -u origin main
```

If you plan to publish this publicly, add a license before pushing.

## Notes

- The repository packages only the mentor skill, not the copilot skill.
- The shared-memory references are included so the skill remains self-contained.
- The persona source packs are designed to internalize judgment rules rather than imitate named individuals.
