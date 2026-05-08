# Claude research review decisions

## Summary

Claude's `claude_tips/` package is valuable, especially for MVP discipline, event structure, prompt workflows, setup checklists, and asset sourcing. It is not the project authority. The authority is now:

1. `.github/copilot-instructions.md`
2. `docs/ARCHITECTURE.md`
3. `docs/SCOPE.md`
4. `docs/ADRs/ADR-001-stack.md`

## Accepted

- Keep MVP small and playable.
- Use scope-control files: `SCOPE.md` and `IDEAS_LATER.md`.
- Use ADRs for new dependencies.
- Use scene/system/data/UI separation.
- Keep business logic out of scenes.
- Use data-driven event JSON with weighted outcomes.
- Use "blue option" style requirements for better player agency.
- Use HTML/CSS overlays where they improve management UI and accessibility.
- Use focused prompt files for repeated workflows.
- Use high-signal code review prompts.
- Treat `mechanika/` as a future source of gameplay truth.

## Rejected

- Hard requirement for Phaser 3.
- Hard ban on Phaser 4.
- `idb-keyval` as the main save abstraction.
- Treating Capacitor as impossible forever.
- Treating external ChatGPT mentor workflow as required.
- Implementing BattleScene/BattleSystem before `mechanika/`.

## Deferred

- Battle mechanics.
- Crew trait effects.
- Crew XP/progression.
- Morale formulas.
- Quest and faction systems.
- Seedable RNG dependency.
- Capacitor evaluation.
- Playwright E2E test suite.

## Action taken

Project source-of-truth files were created in the project root, not inside `claude_tips/`.

The `claude_tips/` folder should remain as reference material only.
