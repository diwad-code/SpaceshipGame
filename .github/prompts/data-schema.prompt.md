---
name: data-schema
description: 'Create or update JSON data schemas and TypeScript types for game content.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runTests
---

# /data-schema

Create or update the data schema for: `${input:schemaName}`.

Rules:

- Put Zod schemas in `src/data/schemas/`.
- Export TypeScript types with `z.infer`.
- Keep schemas compatible with JSON content.
- Include validation errors that are useful during Boot/Preload.
- Do not encode final combat, trait, progression, quest, faction, or morale formulas before `mechanika/`.
- Add minimal tests if validation behavior is non-trivial.
