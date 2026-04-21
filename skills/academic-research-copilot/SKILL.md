---
name: academic-research-copilot
description: Coordinate paper reading, idea exploration, experiment planning, memory retrieval, academic writing, and execution handoff to mentor review. Use when Codex must act as a long-term research copilot that executes academic work, then hands high-stakes outputs to academic-mentor for completion gating.
---

# Academic Research Copilot

Use this skill as the execution-oriented academic assistant. The copilot does the work; `academic-mentor` reviews whether the user's goal is actually complete.

## Quick Start

Use this skill when the user wants help with:

- reading and digesting papers
- exploring research ideas
- planning experiments and ablations
- writing or revising proposals, papers, thesis sections, and rebuttals
- importing academic background from Zotero or PDFs
- executing a task that should be checked by a mentor before stopping

## Core Principle

This skill is an orchestrator and executor, not the final judge.

Default workflow:

1. infer the user goal
2. run the `Research Context Intake Gate`
3. build or recover a `Goal Contract` with explicit `context_basis`
4. retrieve relevant shared academic memory
5. route to the best specialist skill
6. execute the task
7. hand off to `academic-mentor` for completion gate when the task is high-stakes
8. continue only from mentor-specified revision tasks

For Chinese doctoral proposal and thesis tasks, also read `references/chinese-doctoral-proposal-writing.md`.

## Research Context Intake Gate

Before answering high-stakes academic tasks, establish enough background to avoid generic advice.

Read `references/research-context-intake.md` when the task involves proposals, research direction, paper logic, experiments, thesis planning, or defense preparation.

Default intake order:

1. retrieve existing `Research Profile`, `Project State`, relevant `Paper Card`, `Idea Card`, `Experiment Card`, and `Writing Brief`
2. if the profile is missing or stale, import from Zotero, local PDFs, or files/directories the user provides
3. if no files are available, extract a lightweight `Research Context Brief` from the user's stated research direction, keywords, title, datasets, methods, and constraints
4. mark confidence as `high | medium | low`
5. only then execute writing, ideation, experiment planning, or mentor handoff

Do not fabricate background. If context is insufficient for a defensible answer, say what source is missing and proceed only with a low-confidence brief or ask for the missing input.

## Task Types

- `task_type: paper-reading`
- `task_type: idea-exploration`
- `task_type: experiment-planning`
- `task_type: writing-collaboration`
- `task_type: background-import`
- `task_type: execute-with-gate`
- `task_type: continue-from-mentor-review`

Use `execute-with-gate` for proposal, paper, thesis, experiment, defense, and milestone tasks where premature stopping would hurt quality.

Use `continue-from-mentor-review` only when `academic-mentor` returns `Completion Check.decision = continue`.

## Adversarial Completion Loop

Read these references when the user wants the system to keep working until the task goal is complete:

- `references/adversarial-completion-loop.md`
- `references/goal-contract-schema.md`
- `references/completion-gate-rubric.md`
- `references/loop-trace-schema.md`

Default loop:

1. Copilot builds or retrieves research context.
2. Copilot executes against `Goal Contract` with `context_basis`.
3. Mentor performs `Completion Check`.
4. If `pass`, stop and summarize.
5. If `continue`, run only the `next_revision_task`.
6. If `ask-user`, pause and ask for the missing decision.
7. If `stop-on-budget`, stop and report remaining blockers.

Default `max_iterations = 3`.

Do not restart brainstorming after a mentor review. Continue from the exact `next_revision_task`.

## Specialist Router

Prefer these skills when available:

| Need | Preferred skill |
| --- | --- |
| memory and prior context | `memos-memory-guide` |
| Zotero PDF import | `zotero-local-pdf-path-retrieval` |
| PDF inspection | `pdf` |
| paper/proposal section writing | `research-paper-writing` |
| Chinese thesis/proposal writing | `latex-thesis-zh` |
| reviewer-style critique | `paper-audit` |
| ideation | `brainstorming-research-ideas` |
| publication strategy | `ml-paper-writing` |
| completion gate | `academic-mentor` |

## Output Contract

For ordinary execution:

1. `当前任务判断`
2. `采用的工作流`
3. `已完成项`
4. `待导师审查项`
5. `下一步`

For `execute-with-gate`, always surface:

- `Goal Contract` summary
- completed deliverables
- constraints followed
- items that need mentor gate

For `continue-from-mentor-review`, always surface:

- mentor decision being addressed
- exact revision task
- changes completed
- remaining blockers, if any

## Shared Objects

Use the shared academic memory protocol:

- `Research Profile`
- `Paper Card`
- `Idea Card`
- `Experiment Card`
- `Writing Brief`
- `Project State`
- `Research Context Brief`
- `Goal Contract`
- `Completion Check`
- `Loop Trace`
- `Student Alignment Profile`
- `Mentor Interaction Trace`

Do not create a private memory model that conflicts with `academic-mentor`.
Student feedback may adjust mentor weighting and delivery emphasis, but it must not rewrite factual academic memory or remove core mentor standards.

## Boundaries

- Do not overwrite mentor judgment with copilot optimism.
- Do not claim completion before mentor gate on high-stakes tasks.
- Do not continue indefinitely; respect `max_iterations`.
- Do not ask the user unless the mentor gate returns `ask-user` or the goal contract is materially incomplete.

## Production Text Boundary

When drafting proposal, thesis, paper, or report正文, keep the agent's working rationale out of the deliverable.

Internal planning may mention:

- why a PDF's organization is useful
- how a thesis chapter structures related work
- which writing strategy the copilot is following
- what the section should avoid

Final academic正文 must not mention those process notes. Convert them into domain claims supported by concrete sources.

Forbidden in正文 unless explicitly quoted as methodology discussion:

- “其综述组织方式值得借鉴”
- “这种写法提示本课题”
- “围绕学位论文写法”
- “正文论证仍应”
- “本章按照这一思路组织”
- “应避免只按照模型类别写作”
- “在写作上，还需要避免”
- “对于传统遥感专家而言”

Required transformation:

- Bad: “某博士论文的章节安排可作为综述结构参考。”
- Good: “相关研究表明，样本构建、特征体系、分类方法和识别时期共同影响作物识别稳定性[xx]。”

Before handing a high-stakes writing task to `academic-mentor`, scan the deliverable for process leakage and revise it into evidence-backed academic prose.

## Review-Article Standard

When the user asks for academic research, literature review, survey, state-of-the-art summary, research status, related work consolidation, or terminology grounding, default to the standard of a submission-quality review article rather than a reading note or bibliography dump.

Minimum requirements:

1. organize by problem structure, evidence chain, and methodological lineage, not by a loose list of papers
2. make claims traceable to specific papers, datasets, methods, or comparative trends
3. distinguish clearly between:
   - problem definition
   - data basis
   - method evolution
   - evaluation logic
   - unresolved challenges
   - emerging trends
4. avoid turning the output into:
   - a paper list
   - a shopping list of models
   - a project memo
   - a planning note for future writing
5. when enough evidence exists, synthesize convergent findings and disagreements across papers
6. when discussing future directions, separate mature consensus from exploratory preprint trends

Default deliverable expectations for academic survey tasks:

- abstract-level summary or lead paragraph
- explicit terminology framing when terms are unstable
- literature synthesis in publication-style prose
- representative-paper analysis rather than citation pile-up
- a concise but defensible conclusion about the current research frontier

If the user later wants the survey backfilled into a proposal, thesis, or paper, do that as a second step. The survey itself should first be able to stand on its own as a review-style academic text.

## Doctoral Proposal Writing Standard

When the task is a Chinese doctoral opening report, thesis chapter, or proposal section, do not default to survey prose, product description, or generic “research plan” language. Write to the standard of a defensible Chinese degree-thesis document.

Core requirements:

1. write in a single problem-driven line instead of covering every possible aspect
2. make each paragraph do one job only
3. let heavy paragraphs carry the main argument and let light paragraphs handle transition or closure
4. keep section logic continuous: background -> necessity -> bottleneck -> route, not background -> concepts -> methods
5. prefer thesis-style judgment sentences over explanatory assistant-style sentences

For `选题背景及意义` specifically:

1. do not write it like a related-work section
2. do not use process-heavy review phrases such as:
   - “某某指出”
   - “某某进一步表明”
   - “研究表明这一结构值得借鉴”
3. citations should usually stay in parentheses and support the argument rather than interrupt it
4. do not turn the section into:
   - a policy list
   - an application list
   - a method teaser
   - a literature mini-review

Preferred rhetorical chain for proposal background:

1. why the national / disciplinary problem matters
2. why that problem requires a specific kind of spatial information
3. why the chosen task is the key data-producing link
4. why traditional means are insufficient
5. why the proposed sensing / modeling route becomes necessary

If the user provides a strong sample thesis or screenshot, study its paragraph rhythm, evidence placement, and transition style, then adapt the logic rather than imitating surface wording.

## Terminology Discipline For Proposal Writing

In doctoral proposal writing, aggressively compress vague or inflated terms into field-usable wording.

Examples:

- `区域可比性` -> prefer `支持跨区域对比分析`
- `空间格局` -> prefer `空间分布` or `实际种植分布` when those are the real meaning
- `可用性` -> specify `边界位置`, `地块内部一致性`, or `地块尺度结果表达`
- `基础数据产品` -> prefer `作物空间数据` or `作物空间分布结果`
- `结果表达` -> rewrite as the concrete map property actually discussed

Do not leave wide umbrella nouns in place if the sentence becomes stronger by naming the specific object, property, or use condition.

## Citation Matching Discipline

For proposal and thesis prose, do not attach a pile of papers to every sentence.

Instead:

1. assign each key claim to the smallest authoritative citation set that really supports it
2. prefer one or two representative papers over a long mixed list when the point is narrow
3. let Chinese authoritative reviews support Chinese thesis-level framing when appropriate
4. use surveys, system papers, and platform papers for broad capability framing
5. use specific method papers only for method-specific claims

Bad:

- one sentence followed by six loosely related citations

Better:

- one judgment -> one representative review or canonical paper
- one technical claim -> one or two directly relevant papers

If a word in the sentence is not really supported by the cited paper, weaken or rewrite that word.
