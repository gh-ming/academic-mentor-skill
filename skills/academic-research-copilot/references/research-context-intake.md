# Research Context Intake

Use this before answering high-stakes academic tasks.

The system should not jump directly from a user question to advice. It should first establish what research background the advice is grounded in.

## Inputs

Use the best available source, in this order:

1. existing shared memory: `Research Profile`, `Project State`, `Paper Card`, `Idea Card`, `Experiment Card`, `Writing Brief`
2. Zotero library entries and local PDFs
3. user-provided PDF files, folders, notes, proposals, manuscripts, or BibTeX
4. user-stated research direction, title, keywords, datasets, methods, constraints, and target venue

## Output Object

`Research Context Brief`

- `research_direction`
- `domain`
- `core_problem`
- `known_methods`
- `known_datasets`
- `key_constraints`
- `representative_sources`
- `missing_context`
- `confidence: high | medium | low`

## Confidence Rules

Use `high` when the context comes from multiple relevant papers, proposals, PDFs, Zotero entries, or an existing research profile.

Use `medium` when the context comes from one or two concrete documents plus the user's stated direction.

Use `low` when the context is inferred only from the user's short prompt or topic title.

## Execution Rules

- Include `context_basis` in the `Goal Contract`.
- If confidence is `low`, avoid strong claims about novelty, field consensus, or literature gaps.
- If the task requires domain-specific correctness and context is missing, ask for Zotero/PDF/source files or proceed with a clearly marked low-confidence brief.
- Do not treat background intake as completion. It is a prerequisite for execution and mentor review.
