# SpaceshipGame / Star Search

Retro pixel-art game about managing a spaceship mission searching for life. The player manages crew, ship systems, missions, resources, and random incidents. The project is browser-first and targets Android through PWA installation first, then Trusted Web Activity when a Play Store release is justified.

## Current status

Pre-initialization / Sprint 0. No production code has been scaffolded yet. The `claude_tips/` folder is treated as reference material, not project source of truth. The `mechanika/` folder is reserved for the final gameplay mechanics specification and currently must not be invented around.

## Approved stack

| Layer | Decision |
|---|---|
| Engine | Phaser 4 |
| Language | TypeScript, strict mode |
| Build tool | Vite |
| Delivery | PWA first, TWA later for Google Play |
| Save system | IndexedDB through Dexie.js |
| Data validation | Zod |
| Testing | Vitest for core logic, Playwright after MVP |

## Documentation

- `docs/ARCHITECTURE.md` — approved architecture and integration points for future mechanics.
- `docs/SCOPE.md` — what is and is not in the MVP.
- `docs/IDEAS_LATER.md` — deferred ideas and scope-control list.
- `docs/COPILOT_WORKFLOW.md` — natural-language guide for using `/prompt-game-dev`, `/prompt-new-scene`, `/prompt-new-system`, and related prompts.
- `docs/ADRs/ADR-001-stack.md` — stack decision record.
- `SKILLS_RECOMMENDATIONS.txt` — curated good-plus set of recommended skills and MCP servers for the repo.
- `.github/copilot-instructions.md` — always-on Copilot project rules.
- `mechanika/00-template-do-wypelnienia.md` — form to fill in with final gameplay mechanics.

## Next step

Use the project Copilot assets first, then scaffold the codebase:

1. Run `/prompt-game-dev` in Copilot Chat after opening this folder in VS Code.
2. Let it verify project foundations.
3. Scaffold the Vite + Phaser project only after the documentation and `.github/` assets are in place.
