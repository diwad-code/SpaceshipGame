# Creative inputs and external reference materials

## Cel dokumentu

Ten dokument wyjaśnia, jak korzystać z nowych materiałów w `dodatki/` bez mieszania ich z właściwym source of truth projektu.

## Krótka zasada

- `dodatki/research/` = materiał kreatywny i researchowy.
- `dodatki/skills/` = zewnętrzna biblioteka surowych skilli do przeglądu.
- `docs/`, `mechanika/` i `.github/skills/` = właściwe miejsce na zatwierdzone wyniki pracy.

## Hierarchia ważności

Gdy materiały się różnią, obowiązuje taka kolejność:

1. `.github/copilot-instructions.md`
2. `docs/ARCHITECTURE.md`, `docs/SCOPE.md`, `docs/ADRs/`
3. `docs/GAME_BRIEF.md`, `docs/FABULA.md`, `docs/GDD.md`
4. `mechanika/` po jej zatwierdzeniu
5. `dodatki/research/`, `dodatki/skills/`, `claude_tips/` jako materiały pomocnicze

## `dodatki/research/`

Ten folder służy jako kreatywny pakiet wejściowy do dalszej pracy nad grą.

### Aktualna zawartość

- `00-RESEARCH-KONTEKST.md` — baza naukowa i liczby referencyjne do klimatu oraz przyszłych mechanik.
- `01-PROPOZYCJE-MECHANIK.md` — prompt do iteracji nad wariantami mechanik poza repo.
- `02-IMPLEMENTACJA-W-REPO.md` — prompt do późniejszego wypełniania `mechanika/` po zatwierdzeniu decyzji.

### Jak używać

1. Użyj researchu do zbierania inspiracji i pytań projektowych.
2. Zatwierdzone wnioski przepisz do właściwych dokumentów repo.
3. Nie traktuj tego folderu jako automatycznej zgody na nowe mechaniki.
4. Jeśli temat dotyczy kanonu fabularnego, zapisz wynik w `docs/FABULA.md`.
5. Jeśli temat dotyczy briefu lub designu, zapisz wynik w `docs/GAME_BRIEF.md` albo `docs/GDD.md`.
6. Jeśli temat dotyczy finalnych reguł gry, przenieś go dopiero do `mechanika/`.

## `dodatki/skills/`

Ten folder przechowuje importowane lub zebrane zewnętrzne skille, które mogą pomóc przy:

- projektowaniu mechanik,
- pracy nad fabułą i tonem,
- pixel-arcie i prezentacji,
- narzędziach GitHub/workflow,
- szerszym researchu designowym.

### Ważna zasada

Skille z `dodatki/skills/` nie są aktywnymi skillami repozytorium tylko dlatego, że zostały tam skopiowane.

### Jak używać

1. Wybierz konkretny skill z `dodatki/skills/`.
2. Oceń, czy pasuje do zasad SpaceshipGame i aktualnej bramki projektu.
3. Jeśli ma wejść do workflow, zaadaptuj go do `.github/skills/incoming/`.
4. Dopiero po adaptacji i opisaniu w dokumentacji przenieś go do aktywnego `.github/skills/{nazwa}`.

## Zalecany przepływ pracy

1. Przejrzyj `dodatki/research/` jako materiał wejściowy.
2. Uporządkuj decyzje w `docs/GAME_BRIEF.md`, `docs/FABULA.md` i `docs/GDD.md`.
3. Wybierz tylko te skille z `dodatki/skills/`, które realnie wspierają bieżący etap.
4. Adaptuj wybrane skille przez `.github/skills/incoming/`, a nie przez bezpośredni import do aktywnych skilli.
5. Aktualizuj `README.md` i workflow docs, gdy któryś materiał staje się częścią standardowej pracy.
