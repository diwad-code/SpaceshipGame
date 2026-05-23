# PROMPT 02 — Uzupełnienie plików `mechanika/` w repo

> **Instrukcja użycia**: Użyj DOPIERO po zatwierdzeniu mechanik z PROMPT 01.
> Wklej jako nową wiadomość w tym samym czacie. Kontekst rozmowy musi być zachowany.

---

## KONTEKST PROJEKTU

Projekt: **SpaceshipGame / Star Search** — retro pixel-art space management + RPG dice-check.
Setting: rok 2099, pierwsza załogowa misja poszukiwania życia.

**Stack (ważne dla interfejsów TypeScript!):**
- Engine: **Phaser 4** (NIE Phaser 3)
- Language: TypeScript strict mode
- Saves: **Dexie.js** over IndexedDB (NIE idb-keyval)
- Data validation: **Zod**
- Dane gry: JSON w `src/data/`, walidowane Zodem przy boocie

**Autorytety projektu (hierarchia):**
1. `mechanika/` — finalna specyfikacja mechanik (właśnie to wypełniamy)
2. `docs/SCOPE.md` — granice MVP
3. `docs/ADRs/` — decyzje techniczne
4. `.github/copilot-instructions.md` — reguły Copilota

**Czego NIE implementować do czasu uzupełnienia `mechanika/`:**
- formuły walki, damage, enemy AI
- efekty traitów
- krzywe XP/progresji
- quest-chain logic
- szczegółowe formuły morale

---

## PLIKI DO UZUPEŁNIENIA

Folder `mechanika/` zawiera następujące pliki. Uzupełniaj je w tej kolejności:

```
mechanika/
├── README.md                    ← zaktualizuj na końcu
├── 00-template-do-wypelnienia.md ← POMIŃ (szablon pomocniczy, nie dotykamy)
├── 00-overview.md               ← KROK 1
├── 01-game-flow.md              ← KROK 2
├── 02-screens-and-scenes.md     ← KROK 3
├── 03-resources.md              ← KROK 4
├── 04-crew.md                   ← KROK 5
├── 05-ship-systems.md           ← KROK 6
├── 06-missions.md               ← KROK 7
├── 07-events.md                 ← KROK 8
├── 08-progression.md            ← KROK 9
├── 09-failure-and-game-over.md  ← KROK 10
├── 10-balancing-notes.md        ← KROK 11
└── 99-open-questions.md         ← KROK 12
```

---

## PYTANIA PRZED STARTEM

Odpowiedz zanim zaczniesz uzupełniać pliki:

1. **Rozmiar załogi aktywnej**: 5, 8, czy 12 osób? (bez hibernowanych)
2. **Tryb gry**: jeden protagonista (grasz konkretną postacią) czy zarządzanie całą załogą?
3. **Hibernacja/torpor**: tak/nie w MVP?
4. **Permadeath**: tak/nie? Czy jest slot na zapis / kontynuacja?
5. **Czas jednej sesji**: ~30 minut / ~2 godziny / bez limitu?
6. **Kampania vs roguelike**: story mode z checkpointami, czy każda gra od nowa?

---

## ZASADY PRZY UZUPEŁNIANIU

1. **Dane liczbowe z researchu** — używaj konkretnych wartości, np.:
   - promieniowanie: 1,81 mSv/dzień
   - utrata kości: 1,5%/miesiąc
   - recyrkulacja wody: 98%
   - limit dawki NASA: 470/620 mSv
   - nie "niskie/wysokie" — konkretne liczby

2. **Każda wartość gameplay = zakotwiczona w nauce** — obok liczby podaj skrótowe uzasadnienie

3. **Tabele wypełniaj kompletnie** — każda kolumna, każdy wiersz. Puste = `TODO` z pytaniem

4. **Spójność z zatwierdzonymi mechanikami** z PROMPT 01 — żadnych nowych pomysłów

5. **Kompatybilność z Zod + Phaser 4**:
   - sekcje "Dane JSON" → struktury kompatybilne z Zod schema
   - interfejsy TypeScript → strict mode (brak `any`)
   - nazwy pól → camelCase, PascalCase dla klas/interfejsów

6. **Granice MVP** (per `docs/SCOPE.md`):
   - NIE pisz formuł walki
   - NIE pisz efektów traitów
   - NIE pisz XP/progresji
   - Zamiast tego: `// TODO: pending mechanika/ — implementacja po uzupełnieniu sekcji XX`

---

## FORMAT KAŻDEGO PLIKU

Dla każdego pliku dostarczaj **pełną zastępczą zawartość** (od # tytułu do końca).
Nie edytuj fragmentarycznie — podaj cały plik gotowy do skopiowania.

Format odpowiedzi:

```
---
## ✍️ Plik: mechanika/XX-nazwa.md

[PEŁNA ZAWARTOŚĆ PLIKU — gotowa do skopiowania i wklejenia]

---
✅ Czy zatwierdzić i przejść do następnego?
```

---

## SZCZEGÓŁOWE INSTRUKCJE PER PLIK

### `00-overview.md`
Uzupełnij:
- Opis gry 5–10 zdań (klimat, cel, emocje: samotność + nadzieja + survival)
- Cel gracza: dotrzeć, zbadać, wrócić (lub nie?)
- Tabela inspiracji: FTL (event system) + Disco Elysium (dice-check) + Oxygen Not Included (ECLSS) + This War of Mine (moralny ciężar)
- Klimat: twarda SF 2099, realizm, izolacja, odroczony czas

### `01-game-flow.md`
Uzupełnij:
- Główna pętla 8–12 kroków (oparcie na zatwierdzonych mechanikach z PROMPT 01)
- Momenty autosave (Dexie.js): po każdej decyzji, po każdym evencie, po każdym time-skipie
- Co kończy jedną turę: wybór gracza zatwierdza → system rozlicza → stan zapisany
- Uwzględnij mechanikę czasu (time-skip / torpor — zależnie od odpowiedzi na pytania)

### `02-screens-and-scenes.md`
Uzupełnij tabelę ekranów. Sceny MVP (per `docs/SCOPE.md`):
- BootScene, PreloadScene, MainMenuScene, BridgeScene, MapScene, EventScene, CrewScene
- BattleScene = STUB ONLY (jeden wiersz: `// TODO: pending mechanika/`)
- Dodaj tekst intro (klimatyczny, nawiązujący do misji 2099)
- Ton narracji: chłodny, naukowy, ale ludzki. Kosmiczne osamotnienie.

### `03-resources.md`
Uzupełnij tabelę z KONKRETNYMI wartościami z researchu:
- Fuel (paliwo fuzyjne D/³He) — jednostka: tony metryczne
- Oxygen — jednostka: % (realne: odzysk 93% ECLSS)
- Water — jednostka: % recyrkulacji (realne: 98% NASA 2023)
- Food — jednostka: osobodni
- Parts (części zamienne) — jednostka: punkty
- LifeData (dane naukowe z planety) — jednostka: gigabajty (ograniczone bandwidth)
- CrewHealth i CrewMorale NIE są zasobami — to parametry załogi (osobny plik)

Dla każdego zasobu: co przy 0? Jaki trigger eventu?

### `04-crew.md`
Uzupełnij z danych Mars-500, NASA Twin Study, researchu:

**Role** (uzupełnij zależnie od odpowiedzi na pytanie o wielkość załogi):
- Commander / Zastępca (cross-trained pilot)
- Chief Engineer (ECLSS, napęd, naprawy)
- Medical Officer (chirurgia + psychiatria — jedna osoba!)
- Astrobiologist (kontakt z życiem, biosygnatury)
- Pilot / Navigator
- AI Systems Operator
- Botanist (hydroponika, żywność)
- Geologist / Chemist (analiza planety)

**Parametry postaci** — KONKRETNE SKALE z uzasadnieniem naukowym:
- Health: 0–100 (utrata 1,5 pkt/miesiąc bez graw — NASA Twin Study)
- Morale: 0–100 (third-quarter trigger: trigger przy <40 w okolicach 50–75% misji)
- Radiation: 0–620 mSv kumulatywnie (limit NASA; 470 dla kobiet) → powyżej: stały debuff zdrowia
- Fatigue: 0–100 (rośnie bez odpoczynku, spada podczas torporu)

**Umiejętności**: skala 1–10, konkretne do czego służą w dice-check

**Progi morale** — 5 stanów z konkretnymi efektami mechanicznymi

### `05-ship-systems.md`
Uzupełnij z ECLSS (NASA 2023):
- ECLSS-Water: stan 0–100%, awaria przy <10% → event krytyczny
- ECLSS-Oxygen: stan 0–100%, awaria przy <5% → śmierć w godzinach (game over condition)
- ECLSS-CO2: stan 0–100%, awaria → śmierć w godzinach
- ECLSS-Food: stan 0–100%, awaria → głód (długoterminowy)
- FusionReactor: stan 0–100%, degradacja dostarcza wszystkie systemy
- Hull: stan 0–100%, uszkodzenia od pyłu (0,5mm/zdarzenie)
- Sensors: stan 0–100%, wpływa na wykrywanie biosygnatur
- Lab: stan 0–100%, wymagany do analizy życia
- Torpor Chambers: stan 0–100%, awaria = wymuszenie wybudzenia
- Communications: stan 0–100%, bandwidth dla transmisji na Ziemię

Dla każdego: skala, próg awarii, efekt awarii, jak naprawić (zużycie Parts), MVP/później

### `06-missions.md`
Typy misji na planecie po przylocie:
- RemoteSensing (zdalne badanie z orbity) — Sensors + Science
- AtmosphericSampling (pobieranie próbek atmosfery) — Lab + Science
- SurfaceLanding (lądowanie + eksploracja) — Pilot + Engineer + Astrobiolog
- LifeSampleCollection (pobieranie próbek życia) — Astrobiolog + Medical (protokoły COSPAR!)
- QuarantineProtocol (kwarantanna próbek) — Medical + Lab + 72h lockdown
- EmergencyRepair (naprawa systemu) — Engineer + Parts
- CrewWellness (opieka nad załogą) — Medical + Morale

Struktura każdej misji wg szablonu (8 kroków)

### `07-events.md`
Eventy MVP — 15 zdarzeń zainspirowanych researchu:

Eventy w czasie rejsu:
1. Burst promieniowania (solar flare analog) — Radiation wzrost
2. Zderzenie z pyłem (0,1 c+) — Hull uszkodzenie
3. Awaria ECLSS-CO₂ — krytyczny, timer
4. Konflikt załogi (Mars-500 style) — Morale, relacje
5. Third-Quarter Phenomenon — globalne Morale –15
6. Awaria reaktora fuzyjnego — Fuel, Parts
7. Utrata sygnału z Ziemią — Morale, fabularny
8. Nieoczekiwany sygnał radiowy z docelowego układu — fabularny
9. Choroba psychiczna załoganta — Medical check
10. Odkrycie w hibernacji: przebudzenie bez harmonogramu — fabularny

Eventy przy planecie:
11. Fałszywa biosygnatura (DMS jak K2-18b) — narracyjny, naukowy
12. Potwierdzenie atmosfery — fabularny
13. Odkrycie mikrobów — protokół COSPAR
14. Nieoczekiwana pogoda atmosferyczna — Engineering check
15. Skażenie biologiczne próbki — Medical + Lab + kwarantanna

Dla każdego: warunki, tekst (klimatyczny!), 2–3 wybory z dice-check, efekty

### `08-progression.md`
Per `docs/SCOPE.md` — ostrożnie:
- Rozwój załogi: tylko umiejętności (nie XP-curve!) — po sukcesie misji: +0,5 pkt do relevant skill
- Postęp misji życia: 0–100% (trigger po każdym odkryciu)
- Skala odkrycia (0–6 z researchu): mikroby → inteligencja
- BEZ pełnych XP curves, BEZ upgradów statku w MVP

### `09-failure-and-game-over.md`
Uzupełnij warunki:
- ECLSS-Oxygen = 0: natychmiastowy game over (śmierć całej załogi)
- ECLSS-CO₂ krytyczny przez >2h (=tury): game over
- Hull = 0: game over
- Wszyscy poza torporem martwi: game over
- Fuel = 0 przed deceleracją: game over (dryfowanie, narracyjny koniec)
- Morale całej aktywnej załogi = 0: mutiny → game over

Permadeath: decyzja per odpowiedź użytkownika

### `10-balancing-notes.md`
Wartości startowe z uzasadnieniem naukowym:

| Parametr | Wartość | Skąd |
|---|---|---|
| Czas misji (1-way) | 60 lat | Daedalus/Icarus @0,07 c, 4,5 ly |
| Opóźnienie sygnału | 4 lata | prędkość światła |
| Promieniowanie baseline | 1,81 mSv/dzień | RAD/MSL, 16 g/cm² osłony |
| Limit radiacji kobiety | 470 mSv | NASA REID 3% |
| Limit radiacji mężczyźni | 620 mSv | NASA REID 3% |
| Recyrkulacja wody | 98% | NASA BPA 2023 |
| Odzysk O₂ | 93% | Reakcja Sabatiera, ECLSS |
| Utrata kości/miesiąc | 1,5% | NASA Twin Study |
| Third-Quarter trigger | 50–75% misji | Kanas 2021 |
| Event chance per turn | 35% | do wyważenia |

### `99-open-questions.md`
Przejrzyj pytania i zaznacz które zostały rozstrzygnięte przez zatwierdzone mechaniki, które pozostają otwarte, a które są poza MVP.

---

## ZGODNOŚĆ Z `docs/SCOPE.md`

Podczas uzupełniania każdego pliku sprawdzaj:

- ✅ Dozwolone w MVP: resource management, crew roster (role+skills+health+morale), event system, life search progress flag, save/load przez Dexie
- ❌ STUB ONLY: BattleScene, BattleSystem, TraitSystem, ProgressionSystem, quest-chain
- 📋 Zarezerwowane do przyszłości: combat damage, trait effects, XP curves, faction logic

Jeśli mechanika jest poza MVP — wpisz ją jako TODO z odniesieniem do `docs/IDEAS_LATER.md`.

---

## SPÓJNOŚĆ Z `.github/copilot-instructions.md`

Struktury JSON w plikach mechaniki muszą być kompatybilne z regułami Copilota:
- Pola camelCase (np. `lifeSupport`, nie `life_support`)
- Typy nie-null, explicit
- Bez hardkodowanych wartości — wszystko do JSON data files
- Zod-validatable (proste typy: string, number, boolean, array — bez union hell w MVP)

---

*Research naukowy: `00-RESEARCH-KONTEKST.md`. Zatwierdzone mechaniki: patrz wyżej w rozmowie.*
