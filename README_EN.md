# Academic Mentor Skill Repo

[中文](./README.md) | English

A mentor-copilot skill system for PhD research, proposal defense, paper logic, experiment planning, and bounded academic task completion.

What if some of the world's strongest scientists could become your long-term research mentors, guiding your thesis, your research direction, and the way you learn to do science?

Not just answering questions. Not just giving you more papers to read. A real mentor should narrow a vague direction, challenge a method-heavy but problem-light idea, ask whether your evidence supports your claim, and expose the dangerous weaknesses before a proposal defense or thesis defense does.

This repo turns that idea into an installable skill system. One skill works with you as a research copilot: reading papers, organizing knowledge, planning experiments, and drafting academic writing. The other skill acts as a strict mentor: judging research direction, problem definition, evidence quality, and whether the task is truly complete. They are designed to disagree productively: the copilot executes, the mentor reviews, and the system continues when the user's goal has not been met.

It does not impersonate real scientists. It distills research judgment patterns from public papers, courses, interviews, talks, and project pages.

## What You Get

- A long-term research copilot: read papers, organize knowledge, plan experiments, and maintain `Paper Card`, `Idea Card`, `Experiment Card`, and `Writing Brief` objects.
- A strict academic mentor: judge whether a direction is worth doing, whether the problem is clean, whether the method serves the problem, and whether the evidence supports the claim.
- A multi-advisor internal council: one unified mentor voice by default, internally informed by Fei-Fei / Kaiming / Li-Mu style judgment lenses.
- A completion gate: when the goal is not met, the mentor returns `continue`, and the copilot executes only the next concrete revision task. Default maximum loop count is 3.
- An extensible skill repo: source packs, memory protocols, Stop hook adapters, and standalone loop harnesses can be added over time.

## Quick Demo

Suppose you give the system a PhD proposal topic:

```text
Robust Optical Remote Sensing Time-Series Modeling for Large-Scale Crop Mapping
```

A generic assistant may say:

```text
This is a good topic. You can develop it from data, models, and experiments.
```

`academic-research-copilot` first executes:

- organizes background and related papers
- extracts key problems such as crop mapping, optical satellite time series, missing observations, and cross-region generalization
- drafts research questions, technical routes, experiment matrices, and writing briefs
- produces a `Goal Contract` for mentor review

`academic-mentor` then reviews:

- Is the problem clean enough to support a PhD thesis?
- Does the method serve large-scale crop mapping, or is it larger than the problem?
- Do Sentinel-2 / GF-2 data, crop labels, regional transfer, and temporal-missingness experiments support the claims?
- Are any terms wrong for the remote-sensing context, such as an inappropriate object-level transformation?
- If the work is not complete, what exactly must the copilot fix next?

That is the core loop: **Copilot executes. Mentor gates. If the work is not complete, the system continues with a bounded revision task.**

## How It Works

```mermaid
flowchart LR
  U["User Goal"] --> C["academic-research-copilot executes"]
  C --> G["Goal Contract"]
  G --> M["academic-mentor completion gate"]
  M -->|pass| S["Stop and summarize"]
  M -->|continue| R["Revision Task"]
  R --> C
  M -->|ask-user| Q["Ask user"]
  M -->|stop-on-budget| B["Report blockers"]
```

Default workflow:

1. The user provides a research goal, paper section, proposal task, experiment plan, or defense issue.
2. `academic-research-copilot` executes: read, organize, plan, write, revise.
3. `academic-mentor` reviews whether the goal is truly complete.
4. If the mentor returns `continue`, the copilot only fixes the named blocking issue.
5. Default `max_iterations = 3` to avoid infinite runs.

## The Three Advisor Lenses

| Internal advisor lens | What it does not mimic | What it actually does |
| --- | --- | --- |
| `Fei-Fei advisor` | Does not imitate voice or personal speaking habits | Judges research significance, academic framing, narrative coherence, and thesis-worthiness |
| `Kaiming advisor` | Does not imitate compressed personal phrasing | Judges whether the problem is clean, whether the method is necessary, and whether complexity exceeds the problem |
| `Li-Mu advisor` | Does not imitate lecture catchphrases | Decomposes learning paths, experiment routes, minimal validation loops, and next execution tasks |

These lenses are distilled from public papers, project pages, courses, talks, and interviews. They are not three role-play characters. They are internal judgment signals synthesized into one mentor answer by default.

## Installation

Copy both skills into your local skills directory:

```bash
cp -R skills/academic-mentor ~/.codex/skills/
cp -R skills/academic-research-copilot ~/.codex/skills/
```

If you use another agent framework, point it at:

- `skills/academic-mentor/`
- `skills/academic-research-copilot/`

## Usage Examples

```text
Use $academic-research-copilot to read these crop-mapping PDFs and create Paper Cards.
```

```text
Use $academic-mentor to judge whether my PhD proposal topic is defensible.
```

```text
Use $academic-research-copilot to revise my experiment plan, then hand it to $academic-mentor for completion gate.
```

```text
Use $academic-mentor in panel mode to stress-test my defense questions.
```

```text
Use both skills to keep improving this opening report until the mentor returns pass or stop-on-budget.
```

## Who This Is For

- PhD students preparing proposals, thesis chapters, experiments, milestone reports, or defenses.
- Researchers who need strict direction triage rather than generic brainstorming.
- Academic writers who need claim-evidence checking before polishing.
- Agent builders who want a reusable skill-level completion gate before implementing runtime hooks.

## Design Boundaries

- This does not impersonate Fei-Fei Li, Kaiming He, Mu Li, or any real person.
- This is not an automatic science machine; it can review, decompose, and push work forward, but it cannot replace real experiments, advisor feedback, or domain validation.
- This is not an infinite agent loop; the default budget is 3 iterations, after which the system must return `stop-on-budget` and remaining blockers.
- This is not a generic writing polisher; if the problem definition or evidence chain is weak, the mentor points to the root contradiction first.
- The shared memory protocol is defined, but persistent backend integration depends on the host agent framework.

## Repository Goals

This repo does four things:

1. packages `academic-mentor` and `academic-research-copilot` into a dual-skill repo that can be installed or pushed to GitHub directly
2. grounds the mentor in public-source-derived research judgment rules instead of superficial imitation
3. converts the mentor traits inspired by Fei-Fei Li, Kaiming He, and Mu Li into auditable, testable, internally weighted judgment mechanisms
4. upgrades the system into copilot execution plus mentor review, with bounded continuation and feedback-based weighting

## Source Distillation

The repo already includes three source packs:

- `fei-fei-li-source-pack.md`
- `kaiming-he-source-pack.md`
- `li-mu-source-pack.md`

The distillation uses:

- representative papers and project pages
- official homepages and institutional materials
- high-signal public lectures, talks, and videos
- interviews that reveal durable research values

The most important layer is not speech imitation but paper-expression distillation:

- how papers define the real problem
- how papers control contribution boundaries
- how papers organize evidence and experiments
- how papers handle limitations and avoid overclaim

Key materials:

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

See:

- [docs/source-distillation-and-testing.md](./docs/source-distillation-and-testing.md)
- [examples/mode-switch-prompts.md](./examples/mode-switch-prompts.md)
- [tests/academic-persona-eval.md](./tests/academic-persona-eval.md)

## Academic Focus

High-value use cases:

- whether a proposal topic and research content are defensible
- whether a research direction is worth continuing
- whether a paper is solving a real problem
- whether the method is larger than the problem
- whether the experiment chain supports the claim
- where a defense is most vulnerable

The paper pathway is split into two submodes:

- `paper-logic`: judge whether the paper is really solving a real problem and whether the argument stands.
- `paper-strategy`: if the direction is broadly valid, decide what to revise next, what evidence to add, and what to cut or weaken.

## Repository Layout

```text
academic-mentor-skill-repo/
├── README.md
├── README_EN.md
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
    │   ├── SKILL.md
    │   ├── agents/openai.yaml
    │   └── references/
    │       ├── advisor-persona.md
    │       ├── mentor-council.md
    │       ├── source-grounding.md
    │       ├── fei-fei-li-source-pack.md
    │       ├── kaiming-he-source-pack.md
    │       ├── li-mu-source-pack.md
    │       ├── paper-first-distillation.md
    │       ├── adversarial-completion-loop.md
    │       ├── completion-gate-rubric.md
    │       ├── shared-memory-schema.md
    │       └── shared-memory-operations.md
    └── academic-research-copilot/
        ├── SKILL.md
        ├── agents/openai.yaml
        └── references/
            ├── copilot-orchestration.md
            ├── adversarial-completion-loop.md
            ├── goal-contract-schema.md
            ├── completion-gate-rubric.md
            ├── loop-trace-schema.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
```

## Roadmap

1. Keep enriching the three advisor source packs with papers, project pages, talks, videos, and interviews.
2. Add more real academic task tests: proposals, papers, experiment plans, defenses, and milestone reviews.
3. Add an optional Claude Code Stop hook adapter that maps `Completion Check.decision = continue` to a blocked stop event.
4. Add a standalone loop harness for scriptable copilot -> mentor -> copilot execution.
5. Integrate stronger shared memory backends so the mentor can learn the student's research background, recurring failure patterns, and feedback preferences over time.

## Push to GitHub

This repo has already been initialized locally. After reviewing and committing the current changes, publish with:

```bash
git status
git add README.md README_EN.md docs examples tests skills
git commit -m "Add adversarial academic mentor-copilot skills"
git remote add origin <your-repo-url>
git push -u origin main
```
