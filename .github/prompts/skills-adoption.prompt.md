---
name: skills-adoption
description: 'Autonomously execute the approved skills and MCP adoption plan for SpaceshipGame.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - edit/editFiles
  - read/problems
  - execute/runInTerminal
  - execute/runTests
---

# /prompt-skills-adoption

Autonomously execute the approved skills and MCP adoption plan for SpaceshipGame.

## Required inputs

Read these first:

- `README.md`
- `SKILLS_RECOMMENDATIONS.txt`
- `docs/skills-adoption/README.md`
- `docs/ARCHITECTURE.md`
- `docs/SCOPE.md`
- `docs/COPILOT_WORKFLOW.md`
- `mechanika/README.md`
- `.github/prompts/`
- `.github/skills/`

Do not rely on memory alone. Determine the current repository state before editing.

## Operating mode

Work autonomously through the adoption order, but only execute actions that are unblocked by the current repo state.

Use this gate model:

1. **Sprint 0 docs/design gate**
   - Allowed: prompts, docs, local skill scaffolds, mechanika-spec support, architecture/investigate support.
   - Not allowed: implementing unapproved mechanics, adding runtime dependencies without ADRs, or configuring app-only tools before an app exists.

2. **App scaffold gate**
   - Allowed only after `package.json` and `src/` exist.
   - Add Phaser/PWA/browser testing support when it has something real to validate.

3. **CI/release gate**
   - Allowed only after GitHub Actions or release workflows exist.
   - Add CI-fix and changelog automation here.

4. **Design/art pipeline gate**
   - Allowed only when Figma, Phaser Editor, Blender, or another art/design workflow is explicitly adopted.

## Execution rules

- Use the good-plus target set, not a minimum shortlist.
- Prefer local prompts and skills before MCP configuration.
- Do not bulk-import marketplace content.
- For every adopted skill or MCP candidate, document:
  - source,
  - purpose,
  - activation gate,
  - exact files changed,
  - validation performed,
  - remaining blockers.
- Never commit secrets, API keys, personal tokens, or broad external-service configuration.
- Use least-privilege MCP settings and repository-scoped filesystem access where applicable.
- Do not invent combat, trait effects, morale formulas, XP curves, factions, or quest-chain logic before `mechanika/` approves them.
- Keep `README.md` and relevant docs indexes updated.

## Autonomous workflow

1. Inspect current state and list which gates are open or blocked.
2. Build an execution checklist from `docs/skills-adoption/README.md`.
3. Complete all currently unblocked checklist items in order.
4. For blocked items, create clear TODOs in the adoption docs instead of forcing implementation.
5. Run available lint/build/test commands. If none exist, run documentation diff/format checks and explain that no app validation exists yet.
6. Run review/security validation before finishing.
7. End with:

```md
## Skills adoption result
Completed:
Blocked:
Files changed:
Validation:
Recommended next prompt or command:
```
