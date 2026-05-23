---
name: investigate
description: 'Investigates repository state, docs, content gaps, or implementation blockers before making changes.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runInTerminal
  - execute/runTests
---

# /investigate

Use this prompt when you need a focused repo investigation before planning or implementation.

## Read first

Inspect only the files needed for the request, but prefer these sources first:

- `README.md`
- `docs/ARCHITECTURE.md`
- `docs/SCOPE.md`
- `docs/COPILOT_WORKFLOW.md`
- `mechanika/`
- `.github/prompts/`
- `.github/skills/`

## Goals

- Find the current source of truth for the requested area.
- Identify blockers, missing assets, or contradictory docs.
- Recommend the next 1-3 safe actions.

## Rules

- Do not make speculative architecture changes unless asked.
- Do not invent gated mechanics.
- When the repo is still docs-only, prefer docs, prompts, and skill updates over code scaffolding.

## Output

Return:

```md
## Investigation result
Question:
Sources checked:
What is true now:
Blockers:
Recommended next action:
```
