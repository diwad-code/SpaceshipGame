# Instrukcja korzystania z promptów Copilota

English summary: the working custom slash commands are `/game-dev`, `/game-brief`, `/fabula`, `/gdd`, `/skills-adoption`, `/investigate`, `/new-scene`, `/new-system`, `/new-event`, `/data-schema`, `/pwa-check`, `/mobile-ux`, and `/code-review`. Start with `/game-dev`, then lock the brief and story before mechanics-heavy implementation. The detailed guide below is in Polish.

Ten dokument jest prostą instrukcją pracy w VS Code z przygotowanymi promptami projektu SpaceshipGame. Traktuj go jak kolejność rozmowy z Copilotem.

## Najważniejsza zasada

Najpierw używaj promptu **`/game-dev`**. To główny przełącznik projektu. On sprawdza stan repozytorium, przypomina architekturę i mówi, który kolejny prompt ma sens.

Nie zaczynaj od `/new-scene` albo `/new-system`, jeśli nie masz jeszcze gotowego projektu Vite/Phaser i podstawowych folderów.

W obecnym Sprint 0 przed mechaniką najpierw porządkuj: **brief → fabułę → GDD → adoption skills**.

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
| `/fabula` | Gdy tworzysz historię przed mechaniką | Buduje `docs/FABULA.md`: premisę, ton, świat i haki narracyjne |
| `/gdd` | Gdy chcesz utrzymać główny design doc | Aktualizuje `docs/GDD.md` i oznacza sekcje jako approved/reserved/open question |
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

- system dotyczy walki, traits, progresji, morale albo questów,
- folder `mechanika/` nie zawiera jeszcze gotowej specyfikacji tych mechanik.

Wtedy poproś tylko o stub:

```text
/new-system Battle — tylko stub, mechanika będzie później w folderze mechanika
```

### Nie używaj `/new-event`, jeśli:

- event wymaga dokładnych reguł walki,
- event wymaga śmierci załogi,
- event wymaga XP/progresji,
- event wymaga frakcji albo quest-chain.

Do czasu dostarczenia `mechanika/` eventy mają być proste: zasoby, proste uszkodzenia, prosta zmiana zdrowia/morale, postęp misji.

## Harmonogram kolejnych promptów

### Etap 0 — zawsze na start każdej sesji

```text
/game-dev sprawdź stan projektu i podaj następne 1-3 kroki
```

Cel: Copilot ma przypomnieć sobie dokumentację i sprawdzić, czego brakuje.

### Etap 0.25 — brief i fabuła przed mechaniką

Zanim zaczniesz uszczegóławiać mechanikę, ustaw fundament narracyjny:

Jeśli potrzebujesz materiału wejściowego do tej fazy, najpierw przejrzyj:

- `dodatki/research/00-RESEARCH-KONTEKST.md`
- `dodatki/research/01-PROPOZYCJE-MECHANIK.md`
- `docs/CREATIVE_INPUTS.md`

```text
/game-brief uporządkuj krótki brief projektu i misji
```

```text
/fabula przygotuj bazę fabularną, ton i haki narracyjne do docs/FABULA.md
```

```text
/gdd zsynchronizuj brief, fabułę i aktualny scope
```

Cel: repo ma mieć osobne miejsce na wizję produktu, fabułę i design doc zanim zacznie powstawać kod i finalna mechanika.

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

Nie implementuj jeszcze `BattleScene`, chyba że jako stub:

```text
/new-scene Battle — tylko stub z TODO pending mechanika
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

Systemy zależne od przyszłej mechaniki tylko jako stub:

```text
/new-system Battle — tylko stub, bez mechaniki walki
```

```text
/new-system Trait — tylko stub, bez efektów traits
```

```text
/new-system Progression — tylko stub, bez XP curves
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
2. `/game-dev przygotuj projekt Vite + TypeScript + Phaser 4`
3. `/code-review sprawdź setup projektu`
4. `/data-schema resources`
5. `/data-schema crew`
6. `/data-schema ship-systems`
7. `/data-schema events`
8. `/new-scene Boot`
9. `/new-scene Preload`
10. `/new-scene MainMenu`
11. `/new-scene Bridge`
12. `/new-system Resource`
13. `/new-system Save`
14. `/new-system Event`
15. `/new-scene Map`
16. `/new-scene Event`
17. `/new-event drobna awaria napędu`
18. `/new-event opuszczona sonda badawcza`
19. `/pwa-check sprawdź gotowość PWA`
20. `/code-review sprawdź całość po pierwszym działającym loopie`

## Jak pracować, żeby nie zgubić projektu

- Jedna rozmowa = jeden mały cel.
- Jeśli Copilot proponuje dużą przebudowę, poproś: "podziel to na małe kroki".
- Jeśli Copilot chce dodać bibliotekę, poproś: "najpierw ADR".
- Jeśli Copilot zaczyna wymyślać mechanikę walki/progresji, zatrzymaj go i przypomnij: "to czeka na folder mechanika".
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
