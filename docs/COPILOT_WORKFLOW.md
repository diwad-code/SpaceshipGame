# Instrukcja korzystania z promptów Copilota

English summary: the working custom slash commands are `/game-dev`, `/game-brief`, `/fabula`, `/gdd`, `/skills-adoption`, `/investigate`, `/new-scene`, `/new-system`, `/new-event`, `/data-schema`, `/pwa-check`, `/mobile-ux`, and `/code-review`. Start with `/game-dev`, sync docs against `mechanika/`, then scaffold and implement in small steps. The detailed guide below is in Polish.

Ten dokument jest prostą instrukcją pracy w VS Code z przygotowanymi promptami projektu SpaceshipGame. Traktuj go jak kolejność rozmowy z Copilotem.

## Najważniejsza zasada

Najpierw używaj promptu **`/game-dev`**. To główny przełącznik projektu. On sprawdza stan repozytorium, przypomina architekturę i mówi, który kolejny prompt ma sens.

Nie zaczynaj od `/new-scene` albo `/new-system`, jeśli nie masz jeszcze gotowego projektu Vite/Phaser i podstawowych folderów.

W obecnym etapie po domknięciu `mechanika/` najpierw porządkuj: **game-dev → synchronizacja GDD/scope → decyzje blokujące → scaffold projektu**.

## Materiały kreatywne poza source of truth

- `dodatki/research/` traktuj jako pakiet researchowy i kreatywny, nie jako automatycznie zatwierdzoną specyfikację.
- `dodatki/skills/` traktuj jako bibliotekę zewnętrznych skilli do przeglądu.
- Aktywne, repozytoryjne skille nadal mieszkają w `.github/skills/`.
- Jeśli coś z `dodatki/` staje się standardem pracy, zapisz wynik w `docs/`, `mechanika/` albo zaadaptuj skill przez `.github/skills/incoming/`.

## Co oznaczają nasze przełączniki

| Prompt | Kiedy używać | Co robi |
|---|---|---|
| `/game-dev` | Zawsze na początku sesji albo gdy nie wiesz, co dalej | Sprawdza projekt, dokumenty, braki i proponuje następne kroki |
| `/game-brief` | Gdy chcesz ustabilizować wizję projektu | Tworzy lub aktualizuje `docs/GAME_BRIEF.md` bez wchodzenia w szczegółowe mechaniki |
| `/fabula` | Gdy zmienia się kanon albo trzeba dopisać brakującą warstwę narracyjną | Aktualizuje `docs/FABULA.md` bez przepisywania mechaniki |
| `/gdd` | Gdy chcesz utrzymać główny design doc i plan wdrożenia | Synchronizuje `docs/GDD.md` z briefem, fabułą, scope i `mechanika/` |
| `/skills-adoption` | Gdy chcesz wdrożyć zatwierdzony zestaw skills/MCP | Czyta `SKILLS_RECOMMENDATIONS.txt` i `docs/skills-adoption/README.md`, wykonuje odblokowane kroki i raportuje blokery |
| `/investigate` | Gdy najpierw trzeba coś sprawdzić | Robi ukierunkowany research repozytorium, konfliktów i blokerów |
| `/new-scene` | Gdy potrzebujesz nowego ekranu/sceny gry | Tworzy lub planuje scenę Phaser 4, np. `BootScene`, `BridgeScene` |
| `/new-system` | Gdy potrzebujesz nowego modułu logiki gry | Tworzy system TypeScript, np. `CrewSystem`, `ResourceSystem` |
| `/new-event` | Gdy chcesz dodać losowe zdarzenie do gry | Tworzy event data-driven z wyborami i ważonymi wynikami |
| `/data-schema` | Gdy trzeba opisać dane gry i walidację | Tworzy schemat Zod + typy TypeScript |
| `/pwa-check` | Gdy aplikacja ma działać offline lub być instalowalna | Sprawdza manifest, service worker, ikony i cache |
| `/mobile-ux` | Gdy tworzysz lub poprawiasz UI na telefon/tablet | Sprawdza dotyk, layout, rozmiary i pixel-art scaling |
| `/code-review` | Po większym kawałku pracy | Szuka błędów, ryzyk architektury i scope creepu |

## Jak pisać polecenia do Copilota

Pisz krótko i konkretnie. Najlepiej według wzoru:

```text
/nazwa-promptu dokładnie-co-chcę-zrobić
```

Przykłady:

```text
/game-dev sprawdź stan projektu i powiedz co powinienem zrobić jako następne
```

```text
/new-scene Boot
```

```text
/new-system Resource
```

```text
/data-schema crew
```

```text
/new-event awaria systemu podtrzymywania życia
```

```text
/pwa-check sprawdź czy projekt jest gotowy do instalacji na Androidzie jako PWA
```

```text
/code-review sprawdź ostatnie zmiany pod kątem architektury, zapisów i mobile
```

## Kiedy nie używać danego promptu

### Nie używaj `/new-scene`, jeśli:

- nie ma jeszcze projektu Vite/Phaser,
- nie ma folderu `src/scenes/`,
- nie wiesz, czy scena jest w MVP.

Wtedy najpierw użyj:

```text
/game-dev
```

### Nie używaj `/new-system`, jeśli:

- system dotyczy walki, frakcji albo quest-chain poza MVP,
- chcesz dopisać reguły niezatwierdzone jeszcze w `mechanika/99-open-questions.md`.

Wtedy poproś tylko o stub:

```text
/new-system Battle — tylko stub, walka będzie doprecyzowana osobno
```

### Nie używaj `/new-event`, jeśli:

- event wymaga dokładnych reguł walki,
- event wymaga frakcji albo quest-chain,
- event opiera się na parametrze, który nadal jest otwartym pytaniem w `mechanika/99-open-questions.md`,
- chcesz dopisać nową klasę eventu zamiast zaimplementować zatwierdzone eventy z `mechanika/07-events.md`.

Eventy implementuj zgodnie z `mechanika/07-events.md`. Jeśli brakuje decyzji albo parametr zależy od otwartego pytania, zatrzymaj się na danych/stubie zamiast wymyślać nową regułę.

## Harmonogram kolejnych promptów

### Etap 0 — zawsze na start każdej sesji

```text
/game-dev sprawdź stan projektu i podaj następne 1-3 kroki
```

Cel: Copilot ma przypomnieć sobie dokumentację i sprawdzić, czego brakuje.

### Etap 0.25 — synchronizacja po mechanice

Zanim zaczniesz scaffoldować kod, zsynchronizuj dokumenty z gotową mechaniką:

Jeśli potrzebujesz materiału wejściowego do tej fazy, najpierw przejrzyj:

- `dodatki/research/00-RESEARCH-KONTEKST.md`
- `dodatki/research/01-PROPOZYCJE-MECHANIK.md`
- `docs/CREATIVE_INPUTS.md`

```text
/gdd zsynchronizuj brief, fabułę, scope i aktualną mechanikę
```

```text
/investigate wypisz krytyczne blokery implementacji z mechanika/99-open-questions.md
```

Jeśli w trakcie wyjdzie rozjazd:

```text
/game-brief uporządkuj brief zgodnie z aktualną mechaniką
```

```text
/fabula popraw tylko sekcje kanoniczne które rozjechały się z mechaniką
```

Cel: repo ma mieć spójny brief, fabułę, GDD i scope zanim zacznie powstawać kod.

### Etap 0.5 — research i wdrażanie skills/MCP

Gdy chcesz wykonać zatwierdzony rollout skills/MCP:

```text
/skills-adoption wykonaj odblokowane kroki z listy rekomendacji
```

Cel: Copilot ma przejść przez listę, wykonać tylko kroki zgodne z aktualnym stanem repozytorium i zapisać blokery dla etapów wymagających aplikacji, CI albo zewnętrznych usług. Dodatkowe drafty skills wrzucaj najpierw do `.github/skills/incoming/`.

### Etap 1 — przygotowanie projektu technicznego

Gdy będziesz gotowy na stworzenie kodu:

```text
/game-dev przygotuj projekt Vite + TypeScript + Phaser 4 zgodnie z dokumentacją
```

Potem poproś o sprawdzenie:

```text
/code-review sprawdź czy setup projektu nie łamie ADR-001 i copilot-instructions
```

### Etap 2 — dane i schematy

Najpierw dane, potem logika:

```text
/data-schema resources
```

```text
/data-schema crew
```

```text
/data-schema ship-systems
```

```text
/data-schema missions
```

```text
/data-schema events
```

Po każdym większym schemacie:

```text
/code-review sprawdź schematy danych i czy nie ma hardkodowania mechanik
```

### Etap 3 — sceny bazowe

Twórz sceny w tej kolejności:

```text
/new-scene Boot
```

```text
/new-scene Preload
```

```text
/new-scene MainMenu
```

```text
/new-scene Bridge
```

```text
/new-scene Map
```

```text
/new-scene Event
```

```text
/new-scene Crew
```

Na starcie `BattleScene` zostaje stubem:

```text
/new-scene Battle — tylko stub do czasu osobnej decyzji o walce
```

### Etap 4 — systemy gry

Twórz systemy w tej kolejności:

```text
/new-system Resource
```

```text
/new-system Save
```

```text
/new-system Event
```

```text
/new-system Crew
```

```text
/new-system Ship
```

```text
/new-system Mission
```

```text
/new-system LifeSearch
```

Systemy nadal odroczone albo częściowo ograniczone:

```text
/new-system Battle — tylko stub, bez mechaniki walki
```

```text
/new-system Trait — tylko approved hooks, bez pełnego systemu efektów
```

```text
/new-system Progression — tylko zatwierdzona progresja z mechanika, bez szerokich XP curves
```

### Etap 5 — pierwsze eventy

Kiedy masz już schemat eventów i prosty `EventSystem`, dodawaj wydarzenia:

```text
/new-event drobna awaria napędu
```

```text
/new-event opuszczona sonda badawcza
```

```text
/new-event konflikt między członkami załogi
```

```text
/new-event anomalia biologiczna w próbkach
```

Zasada: MVP potrzebuje około 15 prostych eventów, nie 100.

### Etap 6 — PWA i Android

Gdy aplikacja uruchamia się lokalnie:

```text
/pwa-check sprawdź manifest, service worker, cache i instalację na Androidzie
```

Po poprawkach:

```text
/mobile-ux sprawdź główne ekrany pod telefon i tablet
```

### Etap 7 — review po każdym większym kroku

Po każdym ukończonym kawałku:

```text
/code-review sprawdź ostatnie zmiany
```

Jeśli Copilot znajdzie coś poważnego, napraw tylko to, a potem ponów:

```text
/code-review sprawdź czy poprawka rozwiązała problem
```

## Proponowana kolejność pierwszych 20 promptów

1. `/game-dev sprawdź stan projektu i podaj następne kroki`
2. `/gdd zsynchronizuj docs z mechanika v1.0`
3. `/investigate wypisz blokery z mechanika/99-open-questions.md`
4. `/game-dev przygotuj projekt Vite + TypeScript + Phaser 4`
5. `/code-review sprawdź setup projektu`
6. `/data-schema resources`
7. `/data-schema crew`
8. `/data-schema ship-systems`
9. `/data-schema missions`
10. `/data-schema events`
11. `/new-scene Boot`
12. `/new-scene Preload`
13. `/new-scene MainMenu`
14. `/new-scene Bridge`
15. `/new-scene Systems`
16. `/new-scene Torpor`
17. `/new-system Resource`
18. `/new-system Save`
19. `/new-system Mission`
20. `/code-review sprawdź pierwszy działający szkielet loopa`

## Jak pracować, żeby nie zgubić projektu

- Jedna rozmowa = jeden mały cel.
- Jeśli Copilot proponuje dużą przebudowę, poproś: "podziel to na małe kroki".
- Jeśli Copilot chce dodać bibliotekę, poproś: "najpierw ADR".
- Jeśli Copilot zaczyna zmieniać zatwierdzoną mechanikę bez decyzji projektowej, zatrzymaj go i przypomnij: "trzymaj się mechanika/ albo dopisz open question".
- Jeśli coś nie działa, użyj `/code-review` albo poproś `/game-dev` o diagnozę następnego kroku.

## Krótka ściąga

Najczęściej będziesz używać:

```text
/game-dev
/skills-adoption
/new-scene
/new-system
/data-schema
/new-event
/code-review
```

Najpierw budujemy działający loop. Dopiero potem dokładamy większe mechaniki.
