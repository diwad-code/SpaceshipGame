# Instrukcja korzystania z promptów Copilota

Ten dokument jest prostą instrukcją pracy w VS Code z przygotowanymi promptami projektu SpaceshipGame. Traktuj go jak kolejność rozmowy z Copilotem.

## Najważniejsza zasada

Najpierw używaj promptu **`/prompt-game-dev`**. To główny przełącznik projektu. On sprawdza stan repozytorium, przypomina architekturę i mówi, który kolejny prompt ma sens.

Nie zaczynaj od `/prompt-new-scene` albo `/prompt-new-system`, jeśli nie masz jeszcze gotowego projektu Vite/Phaser i podstawowych folderów.

## Co oznaczają nasze przełączniki

| Prompt | Kiedy używać | Co robi |
|---|---|---|
| `/prompt-game-dev` | Zawsze na początku sesji albo gdy nie wiesz, co dalej | Sprawdza projekt, dokumenty, braki i proponuje następne kroki |
| `/prompt-skills-adoption` | Gdy chcesz wdrożyć zatwierdzony zestaw skills/MCP | Czyta `SKILLS_RECOMMENDATIONS.txt` i `docs/skills-adoption/README.md`, wykonuje odblokowane kroki i raportuje blokery |
| `/prompt-new-scene` | Gdy potrzebujesz nowego ekranu/sceny gry | Tworzy lub planuje scenę Phaser 4, np. `BootScene`, `BridgeScene` |
| `/prompt-new-system` | Gdy potrzebujesz nowego modułu logiki gry | Tworzy system TypeScript, np. `CrewSystem`, `ResourceSystem` |
| `/prompt-new-event` | Gdy chcesz dodać losowe zdarzenie do gry | Tworzy event data-driven z wyborami i ważonymi wynikami |
| `/prompt-data-schema` | Gdy trzeba opisać dane gry i walidację | Tworzy schemat Zod + typy TypeScript |
| `/prompt-pwa-check` | Gdy aplikacja ma działać offline lub być instalowalna | Sprawdza manifest, service worker, ikony i cache |
| `/prompt-mobile-ux` | Gdy tworzysz lub poprawiasz UI na telefon/tablet | Sprawdza dotyk, layout, rozmiary i pixel-art scaling |
| `/prompt-code-review` | Po większym kawałku pracy | Szuka błędów, ryzyk architektury i scope creepu |

## Jak pisać polecenia do Copilota

Pisz krótko i konkretnie. Najlepiej według wzoru:

```text
/prompt-nazwa-promptu dokładnie-co-chcę-zrobić
```

Przykłady:

```text
/prompt-game-dev sprawdź stan projektu i powiedz co powinienem zrobić jako następne
```

```text
/prompt-new-scene Boot
```

```text
/prompt-new-system Resource
```

```text
/prompt-data-schema crew
```

```text
/prompt-new-event awaria systemu podtrzymywania życia
```

```text
/prompt-pwa-check sprawdź czy projekt jest gotowy do instalacji na Androidzie jako PWA
```

```text
/prompt-code-review sprawdź ostatnie zmiany pod kątem architektury, zapisów i mobile
```

## Kiedy nie używać danego promptu

### Nie używaj `/prompt-new-scene`, jeśli:

- nie ma jeszcze projektu Vite/Phaser,
- nie ma folderu `src/scenes/`,
- nie wiesz, czy scena jest w MVP.

Wtedy najpierw użyj:

```text
/prompt-game-dev
```

### Nie używaj `/prompt-new-system`, jeśli:

- system dotyczy walki, traits, progresji, morale albo questów,
- folder `mechanika/` nie zawiera jeszcze gotowej specyfikacji tych mechanik.

Wtedy poproś tylko o stub:

```text
/prompt-new-system Battle — tylko stub, mechanika będzie później w folderze mechanika
```

### Nie używaj `/prompt-new-event`, jeśli:

- event wymaga dokładnych reguł walki,
- event wymaga śmierci załogi,
- event wymaga XP/progresji,
- event wymaga frakcji albo quest-chain.

Do czasu dostarczenia `mechanika/` eventy mają być proste: zasoby, proste uszkodzenia, prosta zmiana zdrowia/morale, postęp misji.

## Harmonogram kolejnych promptów

### Etap 0 — zawsze na start każdej sesji

```text
/prompt-game-dev sprawdź stan projektu i podaj następne 1-3 kroki
```

Cel: Copilot ma przypomnieć sobie dokumentację i sprawdzić, czego brakuje.

### Etap 0.5 — research i wdrażanie skills/MCP

Gdy chcesz wykonać zatwierdzony rollout skills/MCP:

```text
/prompt-skills-adoption wykonaj odblokowane kroki z listy rekomendacji
```

Cel: Copilot ma przejść przez listę, wykonać tylko kroki zgodne z aktualnym stanem repozytorium i zapisać blokery dla etapów wymagających aplikacji, CI albo zewnętrznych usług.

### Etap 1 — przygotowanie projektu technicznego

Gdy będziesz gotowy na stworzenie kodu:

```text
/prompt-game-dev przygotuj projekt Vite + TypeScript + Phaser 4 zgodnie z dokumentacją
```

Potem poproś o sprawdzenie:

```text
/prompt-code-review sprawdź czy setup projektu nie łamie ADR-001 i copilot-instructions
```

### Etap 2 — dane i schematy

Najpierw dane, potem logika:

```text
/prompt-data-schema resources
```

```text
/prompt-data-schema crew
```

```text
/prompt-data-schema ship-systems
```

```text
/prompt-data-schema events
```

Po każdym większym schemacie:

```text
/prompt-code-review sprawdź schematy danych i czy nie ma hardkodowania mechanik
```

### Etap 3 — sceny bazowe

Twórz sceny w tej kolejności:

```text
/prompt-new-scene Boot
```

```text
/prompt-new-scene Preload
```

```text
/prompt-new-scene MainMenu
```

```text
/prompt-new-scene Bridge
```

```text
/prompt-new-scene Map
```

```text
/prompt-new-scene Event
```

```text
/prompt-new-scene Crew
```

Nie implementuj jeszcze `BattleScene`, chyba że jako stub:

```text
/prompt-new-scene Battle — tylko stub z TODO pending mechanika
```

### Etap 4 — systemy gry

Twórz systemy w tej kolejności:

```text
/prompt-new-system Resource
```

```text
/prompt-new-system Save
```

```text
/prompt-new-system Event
```

```text
/prompt-new-system Crew
```

```text
/prompt-new-system Ship
```

```text
/prompt-new-system Mission
```

```text
/prompt-new-system LifeSearch
```

Systemy zależne od przyszłej mechaniki tylko jako stub:

```text
/prompt-new-system Battle — tylko stub, bez mechaniki walki
```

```text
/prompt-new-system Trait — tylko stub, bez efektów traits
```

```text
/prompt-new-system Progression — tylko stub, bez XP curves
```

### Etap 5 — pierwsze eventy

Kiedy masz już schemat eventów i prosty `EventSystem`, dodawaj wydarzenia:

```text
/prompt-new-event drobna awaria napędu
```

```text
/prompt-new-event opuszczona sonda badawcza
```

```text
/prompt-new-event konflikt między członkami załogi
```

```text
/prompt-new-event anomalia biologiczna w próbkach
```

Zasada: MVP potrzebuje około 15 prostych eventów, nie 100.

### Etap 6 — PWA i Android

Gdy aplikacja uruchamia się lokalnie:

```text
/prompt-pwa-check sprawdź manifest, service worker, cache i instalację na Androidzie
```

Po poprawkach:

```text
/prompt-mobile-ux sprawdź główne ekrany pod telefon i tablet
```

### Etap 7 — review po każdym większym kroku

Po każdym ukończonym kawałku:

```text
/prompt-code-review sprawdź ostatnie zmiany
```

Jeśli Copilot znajdzie coś poważnego, napraw tylko to, a potem ponów:

```text
/prompt-code-review sprawdź czy poprawka rozwiązała problem
```

## Proponowana kolejność pierwszych 20 promptów

1. `/prompt-game-dev sprawdź stan projektu i podaj następne kroki`
2. `/prompt-game-dev przygotuj projekt Vite + TypeScript + Phaser 4`
3. `/prompt-code-review sprawdź setup projektu`
4. `/prompt-data-schema resources`
5. `/prompt-data-schema crew`
6. `/prompt-data-schema ship-systems`
7. `/prompt-data-schema events`
8. `/prompt-new-scene Boot`
9. `/prompt-new-scene Preload`
10. `/prompt-new-scene MainMenu`
11. `/prompt-new-scene Bridge`
12. `/prompt-new-system Resource`
13. `/prompt-new-system Save`
14. `/prompt-new-system Event`
15. `/prompt-new-scene Map`
16. `/prompt-new-scene Event`
17. `/prompt-new-event drobna awaria napędu`
18. `/prompt-new-event opuszczona sonda badawcza`
19. `/prompt-pwa-check sprawdź gotowość PWA`
20. `/prompt-code-review sprawdź całość po pierwszym działającym loopie`

## Jak pracować, żeby nie zgubić projektu

- Jedna rozmowa = jeden mały cel.
- Jeśli Copilot proponuje dużą przebudowę, poproś: "podziel to na małe kroki".
- Jeśli Copilot chce dodać bibliotekę, poproś: "najpierw ADR".
- Jeśli Copilot zaczyna wymyślać mechanikę walki/progresji, zatrzymaj go i przypomnij: "to czeka na folder mechanika".
- Jeśli coś nie działa, użyj `/prompt-code-review` albo poproś `/prompt-game-dev` o diagnozę następnego kroku.

## Krótka ściąga

Najczęściej będziesz używać:

```text
/prompt-game-dev
/prompt-skills-adoption
/prompt-new-scene
/prompt-new-system
/prompt-data-schema
/prompt-new-event
/prompt-code-review
```

Najpierw budujemy działający loop. Dopiero potem dokładamy większe mechaniki.
