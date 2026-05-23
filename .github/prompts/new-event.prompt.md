---
name: new-event
description: 'Create a data-driven random event with weighted choices and safe MVP effects.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
---

# /new-event

Create a new event for theme: `${input:theme}`.

Before editing:

1. Inspect `src/data/events.json`.
2. Inspect event schemas in `src/data/schemas/`.
3. Keep mechanics-dependent effects simple or mark them as pending `mechanika/`.

Event rules:

- Event IDs use lowercase snake_case.
- Include `title`, `description`, `weight`, `requirements`, and `choices`.
- Choices can include "blue option" style requirements, such as a crew skill threshold.
- Outcomes are weighted.
- MVP effects may change resources, simple crew health, simple morale, mission progress, or ship system health.
- Do not add death, combat, trait, XP, quest-chain, or faction effects until `mechanika/` defines them.
- Keep effects in a range that does not instantly end the run unless explicitly approved.

If event schema files do not exist yet, propose the schema first instead of writing incompatible data.
