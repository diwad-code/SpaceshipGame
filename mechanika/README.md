# Mechanika gry — instrukcja uzupełniania

English summary: start with `00-template-do-wypelnienia.md`, then move refined sections into the numbered files in this folder. The detailed guide below is in Polish.

Ten folder jest miejscem na Twoją specyfikację mechaniki gry. To ona będzie później podstawą dla implementacji systemów takich jak `CrewSystem`, `MissionSystem`, `EventSystem`, `BattleSystem`, `TraitSystem` i `ProgressionSystem`.

## Jak pracować

1. Zacznij od `00-template-do-wypelnienia.md`.
2. Uzupełnij go swobodnie, nawet jeśli część odpowiedzi będzie niepewna.
3. Potem przenieś dopracowane sekcje do osobnych plików:
   - `00-overview.md`
   - `01-game-flow.md`
   - `02-screens-and-scenes.md`
   - `03-resources.md`
   - `04-crew.md`
   - `05-ship-systems.md`
   - `06-missions.md`
   - `07-events.md`
   - `08-progression.md`
   - `09-failure-and-game-over.md`
   - `10-balancing-notes.md`
   - `99-open-questions.md`

## Najważniejsza zasada

Opisuj intencje językiem naturalnym, a wartości liczbowe i reguły w tabelach.

Przykład:

- klimat, fabuła, kolejność scen: język naturalny;
- zasoby, skale morale, umiejętności, efekty eventów: tabele;
- niepewności: lista pytań w `99-open-questions.md`.

Nie musisz uzupełniać wszystkiego od razu. Najpierw najważniejsze są: główna pętla gry, zasoby, załoga, eventy i warunki przegranej.
