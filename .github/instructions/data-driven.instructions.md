---
description: 'Rules for data-driven gameplay models and systems.'
applyTo: 'src/data/**, src/systems/**/*.ts, src/models/**/*.ts, src/types/**/*.ts'
---

# Data-driven architecture instructions

- All gameplay values must come from data files or typed constants approved in docs.
- Use Zod schemas for game data validation.
- Prefer plain serializable objects for state.
- Do not hardcode crew, mission, event, resource, or ship-system values in system logic.
- Keep systems deterministic where practical.
- Effects that depend on combat, traits, progression, morale, quests, or factions are pending `mechanika/`.
- Use simple stubs and TODO comments instead of inventing missing mechanics.
