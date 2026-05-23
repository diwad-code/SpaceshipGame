# Local skills

This directory contains the repository-local skills that Copilot can use for SpaceshipGame.

## Active local skills

- `scaffold-scene` — Phaser 4 scene scaffolding aligned with repo architecture.
- `scaffold-system` — pure TypeScript system scaffolding with serializable state.
- `mechanika-spec` — controlled work inside `mechanika/`.
- `story-bible` — narrative canon and story foundation in `docs/FABULA.md`.
- `skill-creator` — local skill adaptation workflow for this repo.
- `content-research-writer` — grounded documentation authoring for Sprint 0 and beyond.

## Intake flow for additional skills

1. Drop raw or draft material into `.github/skills/incoming/`.
   - If the raw source currently lives in `dodatki/skills/`, copy or adapt only the selected skill instead of treating the whole folder as active.
2. Review whether it fits the repo rules, stack, and current gate.
3. Adapt it into a clean local skill package under `.github/skills/{skill-name}/`.
4. Update `README.md`, `docs/COPILOT_WORKFLOW.md`, and adoption docs if the skill becomes part of the standard workflow.

## Rules

- Prefer adapted local skills over bulk imports.
- Do not treat `incoming/` content as active by default.
- Do not treat `dodatki/skills/` as active by default.
- Record activation gates and blockers for every non-trivial skill.
