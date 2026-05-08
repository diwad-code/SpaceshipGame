---
name: code-review
description: 'High-signal project-specific review for SpaceshipGame changes.'
agent: agent
model: gpt-5.4
tools:
  - search/codebase
  - read/problems
---

# /prompt-code-review

Review the current changes for SpaceshipGame.

Read the actual workspace files before judging. Do not review only this prompt text.
This is a report-only review: do not edit, create, delete, move, or scaffold files.
When VS Code runs a prompt file, its YAML frontmatter can be hidden from the prompt body. Do not flag missing frontmatter unless you actually read the `.prompt.md` file from disk and confirm it is missing there.

Scope:

- [README.md](../../README.md)
- [docs/](../../docs/)
- [mechanika/](../../mechanika/)
- [.github/copilot-instructions.md](../copilot-instructions.md)
- [.github/instructions/](../instructions/)
- [.github/prompts/](../prompts/)
- [.github/agents/](../agents/)
- [.github/skills/](../skills/)

Prioritize:

1. Bugs.
2. Save-data risks.
3. PWA/mobile risks.
4. Architecture violations.
5. Scope creep.

Always flag:

- `localStorage` used for primary save data.
- Business logic inside Phaser scenes.
- Hardcoded gameplay values.
- Missing cleanup of event listeners.
- New dependencies without ADR.
- Mechanics invented before `mechanika/`.
- Phaser 3-only API used in Phaser 4 code.

Return:

```md
## What's good
## Top issues
## Required fixes before next step
```

Do not list minor style issues unless they hide real risk.
