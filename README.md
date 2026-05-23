# SpaceshipGame / Star Search

Retro pixel-art game about managing a spaceship mission searching for life. The player manages crew, ship systems, missions, resources, and random incidents. The project is browser-first and targets Android through PWA installation first, then Trusted Web Activity when a Play Store release is justified.

## Current status

Pre-initialization / Sprint 0. No production code has been scaffolded yet. The `claude_tips/`, `dodatki/research/`, and `dodatki/skills/` folders are treated as reference material, not project source of truth. The `mechanika/` folder is reserved for the final gameplay mechanics specification and currently must not be invented around.

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
- `docs/CREATIVE_INPUTS.md` — how to use the new creative research pack and external skill library in `dodatki/`.
- `docs/GAME_BRIEF.md` — durable product and mission brief before implementation expands.
- `docs/FABULA.md` — story bible and narrative canon kept separate from gameplay rules.
- `docs/GDD.md` — structured design document linking brief, fabula, scope, and mechanika placeholders.
- `docs/SCOPE.md` — what is and is not in the MVP.
- `docs/IDEAS_LATER.md` — deferred ideas and scope-control list.
- `docs/COPILOT_WORKFLOW.md` — natural-language guide for using `/game-dev`, `/game-brief`, `/fabula`, `/gdd`, and related prompts.
- `docs/ADRs/ADR-001-stack.md` — stack decision record.
- `SKILLS_RECOMMENDATIONS.txt` — curated good-plus set of recommended skills and MCP servers for the repo.
- `docs/skills-adoption/README.md` — expanded research and adoption order for skills/MCP rollout.
- `.github/skills/incoming/` — staged recommended skills that are not active yet because they still depend on app, CI, or design-pipeline gates.
- `dodatki/research/` — creative scientific research pack and prompt flow for later mechanika work.
- `dodatki/skills/` — raw external skill library to review before adapting items into `.github/skills/incoming/`.
- `.github/prompts/skills-adoption.prompt.md` — autonomous prompt for executing the skills/MCP adoption plan.
- `.github/copilot-instructions.md` — always-on Copilot project rules.
- `mechanika/00-template-do-wypelnienia.md` — form to fill in with final gameplay mechanics.

## Co dalej?

Ta część ma być aktualizowana na bieżąco, tak aby kolejna osoba mogła przejąć projekt bez wcześniejszego kontekstu.

Aktualnie projekt jest w Sprint 0: porządkowana jest dokumentacja, workflow Copilota i materiały wejściowe. Nie ma jeszcze `package.json`, katalogu `src/` ani uruchamialnej wersji gry. Zestaw rekomendowanych skillów został już rozdzielony na aktywne lokalne skille i staged intake w `.github/skills/incoming/`, żeby przed dalszą pracą nad fabułą było jasne, co jest gotowe teraz, a co czeka na kolejne bramki.

Najbliższe kroki:

1. Otwórz repozytorium w VS Code z włączonym GitHub Copilot Chat.
2. Przeczytaj najpierw:
   - `docs/GAME_BRIEF.md` — czym ma być gra,
   - `docs/FABULA.md` — aktualny kanon fabularny,
   - `docs/GDD.md` — uporządkowany projekt gry,
   - `docs/ARCHITECTURE.md` — zasady techniczne i miejsca przyszłej integracji.
3. Używaj komend Copilota zgodnych z polem `name:` w plikach `.github/prompts/`:
   - `/game-dev` — sprawdzenie stanu repo i wybór kolejnych 1-3 kroków,
   - `/game-brief` — dopracowanie trwałego opisu projektu,
   - `/fabula` — rozwijanie biblii fabularnej przed zamknięciem mechanik,
   - `/gdd` — utrzymanie dokumentu projektowego w zgodzie z briefem i fabułą,
   - `/skills-adoption` — wdrażanie zatwierdzonych skillów i MCP z dokumentacji,
   - `/investigate`, `/new-scene`, `/new-system`, `/new-event`, `/data-schema`, `/pwa-check`, `/mobile-ux`, `/code-review`.
4. W Sprint 0 trzymaj kolejność pracy: `/game-dev` → `/game-brief` → `/fabula` → `/gdd` → `/skills-adoption`. Skill packages wymagające aplikacji, CI albo pipeline'u art nadal zostają w `.github/skills/incoming/` do czasu odblokowania tych bramek.
5. Nie wymyślaj jeszcze szczegółowych mechanik walki, traitów, morale, progresji, frakcji ani łańcuchów questów. Te reguły mają trafić do `mechanika/`, gdy zostaną zatwierdzone.
6. Traktuj `dodatki/research/` i `dodatki/skills/` jako biblioteki wejściowe. Zatwierdzone wnioski przenoś do `docs/`, `mechanika/` albo `.github/skills/`.
7. Dopiero po ustabilizowaniu dokumentacji i assetów `.github/` scaffolduj projekt Vite + Phaser 4.
8. Po każdej większej zmianie aktualizuj tę sekcję: wpisz aktualny stan, najbliższe kroki i blokery, które musi znać osoba kontynuująca pracę.

## If the slash commands do not appear

1. Make sure you opened the repository root in VS Code, not a parent folder.
2. Confirm the prompt files exist in `.github/prompts/`.
3. Use the command names above without the `prompt-` prefix, because Copilot takes the slash command name from each prompt file's `name:` field.
4. Additional draft skills should be staged in `.github/skills/incoming/` before they become active local skills.
5. If VS Code still does not list them, reload the window and try again; as a fallback, open the matching file in `.github/prompts/` and paste its instructions into chat manually.
