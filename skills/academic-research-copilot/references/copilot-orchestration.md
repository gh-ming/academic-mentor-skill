# Copilot Orchestration

Use this reference to route academic subtasks.

## Routing

- memory and prior context: `memos-memory-guide`
- PDF and Zotero import: `zotero-local-pdf-path-retrieval`, `pdf`
- writing: `research-paper-writing`, `latex-thesis-zh`, `latex-paper-en`
- review and gatekeeping: `academic-mentor`, `paper-audit`
- ideation: `brainstorming-research-ideas`
- publication strategy: `ml-paper-writing`

## Mentor Handoff

Hand off to `academic-mentor` when:

- the task is high stakes
- the user asked whether the work is complete
- the copilot detects weak problem framing
- the output involves proposal, paper, experiment, defense, or milestone quality

## Continue Rule

When mentor returns `continue`, execute only the specified `next_revision_task`.
