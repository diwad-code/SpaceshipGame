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
- `docs/GAME_BRIEF.md` — durable product and mission brief before implementation expands.
- `docs/FABULA.md` — story bible and narrative canon kept separate from gameplay rules.
- `docs/GDD.md` — structured design document linking brief, fabula, scope, and mechanika placeholders.
- `docs/SCOPE.md` — what is and is not in the MVP.
- `docs/IDEAS_LATER.md` — deferred ideas and scope-control list.
- `docs/COPILOT_WORKFLOW.md` — natural-language guide for using `/game-dev`, `/game-brief`, `/fabula`, `/gdd`, and related prompts.
- `docs/ADRs/ADR-001-stack.md` — stack decision record.
- `SKILLS_RECOMMENDATIONS.txt` — curated good-plus set of recommended skills and MCP servers for the repo.
- `docs/skills-adoption/README.md` — expanded research and adoption order for skills/MCP rollout.
- `.github/prompts/skills-adoption.prompt.md` — autonomous prompt for executing the skills/MCP adoption plan.
- `.github/copilot-instructions.md` — always-on Copilot project rules.
- `mechanika/00-template-do-wypelnienia.md` — form to fill in with final gameplay mechanics.

## Next step

Use the project Copilot assets first, then scaffold the codebase:

1. Open this folder in VS Code with GitHub Copilot Chat enabled.
2. Use the custom prompt slash commands that match each prompt file `name:` field:
   - `/game-dev` — check repo state and ask for the next 1-3 steps
   - `/game-brief` — create or refine the durable project brief
   - `/fabula` — build the story bible before mechanics solidify
   - `/gdd` — keep the structured design document in sync
   - `/skills-adoption` — execute the approved skills/MCP rollout from the research docs
   - `/investigate`, `/new-scene`, `/new-system`, `/new-event`, `/data-schema`, `/pwa-check`, `/mobile-ux`, `/code-review`
3. In Sprint 0, stabilize the docs flow in this order: `/game-dev` → `/game-brief` → `/fabula` → `/gdd` → `/skills-adoption`.
4. Only scaffold the Vite + Phaser project after the documentation and `.github/` assets are in place.
5. Because this repository is still in Sprint 0, there is no `package.json`, no `src/`, and no runnable npm command yet.

## If the slash commands do not appear

1. Make sure you opened the repository root in VS Code, not a parent folder.
2. Confirm the prompt files exist in `.github/prompts/`.
3. Use the command names above without the `prompt-` prefix, because Copilot takes the slash command name from each prompt file's `name:` field.
4. Additional draft skills should be staged in `.github/skills/incoming/` before they become active local skills.
5. If VS Code still does not list them, reload the window and try again; as a fallback, open the matching file in `.github/prompts/` and paste its instructions into chat manually.
