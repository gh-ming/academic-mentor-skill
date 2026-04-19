# Copilot Orchestration

Use this reference to route academic subtasks.

## Routing

- research context intake: `memos-memory-guide`, `zotero-local-pdf-path-retrieval`, `pdf`
- memory and prior context: `memos-memory-guide`
- PDF and Zotero import: `zotero-local-pdf-path-retrieval`, `pdf`
- writing: `research-paper-writing`, `latex-thesis-zh`, `latex-paper-en`
- review and gatekeeping: `academic-mentor`, `paper-audit`
- ideation: `brainstorming-research-ideas`
- publication strategy: `ml-paper-writing`

## Context-First Rule

Before proposal, paper, experiment, direction, thesis, or defense work:

1. retrieve existing `Research Profile` and `Project State`
2. import Zotero/PDF/user-provided files if the profile is missing or stale
3. if files are absent, draft a `Research Context Brief` from the user's stated direction and mark confidence
4. include `context_basis` in the `Goal Contract`
5. only then execute the academic task

## Mentor Handoff

Hand off to `academic-mentor` when:

- the task is high stakes
- the user asked whether the work is complete
- the copilot detects weak problem framing
- the output involves proposal, paper, experiment, defense, or milestone quality

## Continue Rule

When mentor returns `continue`, execute only the specified `next_revision_task`.
