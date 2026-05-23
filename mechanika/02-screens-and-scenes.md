# 02 — Screens and Scenes
## Ekrany i Sceny | Wersja 1.0

> Lista scen Phaser 4, przepływ między nimi, overlaye HTML/CSS,
> layout mobilny i narracyjny ton każdego ekranu.
> Implementacja: sceny w `src/scenes/`, overlaye w `src/ui/`.
> Stack: Phaser 4 + TypeScript + Vite + PWA.
> Ostatnia aktualizacja: 2026-05

---

## ZASADA NACZELNA

Każda scena ma jedno zadanie.
Sceny orkiestrują rendering i input. Logika gry jest w systemach.
Nigdy odwrotnie.

**Estetyka:** retro-pixel terminal. Interfejs *Kairos* wygląda jak
terminal lat 80. z 2099 roku — bo projektowali go ludzie którzy myśleli
że retro jest wiarygodne. Czarne tło, zielony lub bursztynowy tekst,
pikselowe portrety, minimalizm formy.

---

## 1. LISTA SCEN MVP

| Scena | Klucz | Status | Akt |
|---|---|---|---|
| `BootScene` | `Boot` | Wymagana | — |
| `PreloadScene` | `Preload` | Wymagana | — |
| `MainMenuScene` | `MainMenu` | Wymagana | — |
| `BridgeScene` | `Bridge` | Wymagana | I–V |
| `EventScene` | `Event` | Wymagana | I–V |
| `CrewScene` | `Crew` | Wymagana | I–V |
| `SystemsScene` | `Systems` | Wymagana | I–V |
| `TorporScene` | `Torpor` | Wymagana | I–V |
| `MapScene` | `Map` | Wymagana | I–V |
| `LogbookScene` | `Logbook` | Wymagana | I–V |
| `ApproachScene` | `Approach` | Wymagana | IV |
| `EndingScene` | `Ending` | Wymagana | V |
| `GameOverScene` | `GameOver` | Wymagana | I–V |
| `BattleScene` | `Battle` | **STUB** | — |

---

## 2. DIAGRAM PRZEPŁYWU SCEN

```
[BootScene] → [PreloadScene] → [MainMenuScene]
                                      │
                         ┌────────────┴────────────┐
                         │                         │
                    NOWA GRA                  KONTYNUUJ
                         │                         │
                         └────────────┬────────────┘
                                      │
                               [BridgeScene] ◄──────────────────┐
                              (główny hub)                       │
                                      │                          │
              ┌───────────┬───────────┼───────────┬─────────────┤
              │           │           │           │             │
         [CrewScene] [SystemsScene] [MapScene] [LogbookScene]  │
              │           │           │           │             │
              └───────────┴───────────┴───────────┘             │
                                      │                          │
                              [EventScene]                       │
                          (po fazie Zdarzenie)                  │
                                      │                          │
                               powrót do Bridge ─────────────────┘
                                      │
                              [TorporScene]
                          (koniec każdej tury)
                                      │
                               powrót do Bridge
                                      │
                         ┌────────────┴────────────┐
                         │                         │
                    [ApproachScene]           warunki KG
                      (tylko Akt IV)               │
                         │                         ▼
                    powrót do Bridge         [GameOverScene]
                         │
                    zakończenie misji
                         │
                    [EndingScene]
```

---

## 3. SCENY TECHNICZNE

---

### BootScene

**Zadanie:** Inicjalizacja Dexie.js, walidacja zapisów, routing.

**Co się dzieje:**
1. Inicjalizacja IndexedDB przez Dexie.js
2. Sprawdzenie czy istnieje aktywny zapis (autosave slot)
3. Walidacja schematu zapisu (migracja jeśli starsza wersja)
4. Preload minimalnych assetów (splash screen)
5. Routing: jeśli zapis istnieje → flaga "continue available"

**Przejście:**
→ `PreloadScene` zawsze

**UI:** Ekran czarny, ładujący się pasek postępu (terminal style).
`> INICJALIZACJA SYSTEMU KAIROS...`

---

### PreloadScene

**Zadanie:** Ładowanie wszystkich assetów gry i walidacja Zod.

**Co się dzieje:**
1. Ładowanie sprite'ów, atlasów, audio
2. Ładowanie plików JSON (`events.json`, `crew.json`, `ship-systems.json`)
3. Walidacja Zod wszystkich danych — błąd = crash z czytelnym komunikatem
4. Pasek postępu

**Przejście:**
→ `MainMenuScene` po ukończeniu

**UI:** Terminal loading, zielony tekst, progress bar pikselowy.

---

## 4. MENU GŁÓWNE

---

### MainMenuScene

**Zadanie:** Punkt wejścia gracza. Nowa gra, kontynuacja, logbook.

**Elementy:**
- Tytuł: `MISJA KAIROS` (pikselowy font)
- Podtytuł: `Rok 2099. Lecisz w kierunku Limes.`
- Opcje:
  - `> NOWA MISJA` (zawsze aktywna)
  - `> KONTYNUUJ` (aktywna jeśli istnieje autosave)
  - `> LOGBOOK` (aktywna jeśli istnieje historia)
  - `> WYJŚCIE` (tylko desktop)

**Tło:** Statyczna scena pixelowa — statek *Kairos* na tle gwiazd.
Parallax efekt przy ruchu kursora/dotyku. Bardzo powolny.

**Dźwięk:** Ambientowe, przestrzenne. Jeden delikatny loop.

**Przejście:**
- NOWA MISJA → intro sequence → `BridgeScene` (Tura 0)
- KONTYNUUJ → `BridgeScene` (stan z autosave)
- LOGBOOK → `LogbookScene` (read-only mode)

---

## 5. SCENY GŁÓWNE ROZGRYWKI

---

### BridgeScene *(Mostek — główny hub)*

**Zadanie:** Centrum dowodzenia. Faza 1 (Przebudzenie) i Faza 2 (Przydział) rozgrywki.

**To jest ekran na którym gracz spędza ~70% czasu.**

#### Layout — desktop (expanded ≥840dp)

```
┌─────────────────────────────────────────────────────────────┐
│  KAIROS | AKT II | 23% MISJI | TURA 38 | DZ. 1246          │
├──────────────────┬────────────────────┬─────────────────────┤
│  ZASOBY          │  STATUS STATKU     │  ZAŁOGA             │
│                  │                    │                     │
│  TLEN    ████░   │  Kadłub    ████░   │  Jakub  ■ aktywny  │
│  74/100          │  89%               │  Grzech ■ aktywny  │
│                  │                    │  Yuki   □ torpor   │
│  WODA    ███░░   │  Sensory   ███░░   │  Mira   □ torpor   │
│  63/100          │  71%               │  Amara  □ torpor   │
│                  │                    │  Lena   □ torpor   │
│  ŻYWNOŚĆ ███░░   │  Lab       ████░   │  Felix  □ torpor   │
│  48/100          │  88%               │                     │
│                  │                    │  [SZCZEGÓŁY →]      │
│  PALIWO  █████   │  Medbay    █████   │                     │
│  87/100          │  91%               │                     │
│                  │                    │                     │
│  CZĘŚCI  ████░   │  Comm      ████░   │                     │
│  61/100          │  76%               │                     │
├──────────────────┴────────────────────┴─────────────────────┤
│  ARIA: "CO₂ Scrubber: 71%. Degradacja +1%/turę.            │
│         Sugeruję konserwację. Poza tym — nominalnie."       │
├─────────────────────────────────────────────────────────────┤
│  [PRZYDZIAŁ ZADAŃ]  [MAPA MISJI]  [DZIENNIK]  [SYGNAŁ]     │
└─────────────────────────────────────────────────────────────┘
```

#### Layout — mobile compact (<600dp)

Jeden panel na raz. Dolny pasek nawigacji.

```
┌──────────────────────┐
│  KAIROS | AKT II     │
│  23% | TURA 38       │
├──────────────────────┤
│  [ZASOBY / SYSTEMY]  │  ← tab switcher
│  (aktywna zakładka)  │
├──────────────────────┤
│  ARIA komunikat      │
├──────────────────────┤
│ [ZAD] [ZAŁOGA] [MAP] │  ← bottom nav, 48dp min
└──────────────────────┘
```

**Zachowania:**
- Klik na zasób → ekspansja z historią i tendencją
- Klik na system → `SystemsScene` z focusem na tym systemie
- Klik na załogant → `CrewScene` z focusem na tej postaci
- Klik `PRZYDZIAŁ ZADAŃ` → modal przydziału (bottom sheet na mobile)
- Klik `MAPA MISJI` → `MapScene`
- Klik `DZIENNIK` → `LogbookScene`
- Klik `SYGNAŁ` → modal kompozycji wiadomości do Ziemi

**Przejście po przydziale:**
→ `EventScene` (jeśli event losowany lub FORCED)
→ `TorporScene` (jeśli brak eventu, koniec fazy)

---

### EventScene *(Zdarzenie)*

**Zadanie:** Prezentacja eventu, głosów wewnętrznych, wyborów gracza.

**To jest emocjonalne serce gry.**

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│                    [NARRACJA EVENTU]                        │
│                                                             │
│   Tekst pojawia się powoli (typewriter, 40ms/znak).         │
│   Maksimum 6–8 linii widocznych jednocześnie.               │
│   Scroll możliwy po zakończeniu.                            │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  GŁOSY WEWNĘTRZNE (jeśli skill ≥ 4):                       │
│                                                             │
│  [NAUKA]     „87% prawdopodobieństwo życia biologicznego."  │
│  [PRZETRWANIE] „Zweryfikuj zanim świętujecie."              │
│  [EMPATIA]   „Yuki płacze. Nie widzi że płacze."           │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  [A] Protokół weryfikacji                                   │
│  [B] Pozwól świętować                                       │
│  [C] ░░░░ NIEBIESKI ░░░ Yuki prowadzi protokół             │
│       (wymaga: NAUKA Yuki ≥ 9, Morale Yuki ≥ 60)          │
└─────────────────────────────────────────────────────────────┘
```

**Mechanika typewriter:** tekst pojawia się literka po literce.
Gracz może przyspieszyć (tap/klik) — jeden tap = pełne zdanie,
drugi tap = cały tekst natychmiast.

**Głosy wewnętrzne:**
- Pojawiają się TYLKO gdy wartość skilla ≥ 4
- Każdy głos ma inny kolor/styl (NAUKA: zielony; EMPATIA: niebieski; SYGNAŁ: czerwony, etc.)
- Widoczne po pojawieniu się narracji — nie przerywają tekstu
- Na mobile: ukryte za ikoną, rozwijane na tap

**Blue check (niebieska opcja):**
- Wyróżniona wizualnie (inny kolor tła, ikona gwiazdki)
- Wymogi widoczne gdy zablokowana, ukryte gdy dostępna
  *(gracz sam odczytuje dlaczego może lub nie może)*

**Po wyborze:**
1. Check animacja (jeśli wymagany):
   - Rzut kością: animacja d6 pikselowego, 0.5s
   - Wynik: sukces (zielony flash) / porażka (czerwony flash)
   - Tekst rezultatu

2. Efekty wizualne:
   - Zmiana parametrów postaci: floaty nad portretami
   - Zmiana zasobów: ikony zasobów z deltą
   - Nowe relacje: subtelna ikona serca/pęknięcia

**Przejście:**
→ `BridgeScene` po zamknięciu eventu

---

### CrewScene *(Załoga)*

**Zadanie:** Szczegółowy widok stanu wszystkich 7 członków załogi.

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│  ZAŁOGA KAIROS                           [← MOSTEK]         │
├──────────┬──────────────────────────────────────────────────┤
│  PORTRET │  JAKUB NOWAK — Komandor                          │
│  8×8 px  │  Health:    ████████░░  87/100                   │
│  piksel  │  Morale:    ███████░░░  72/100                   │
│          │  Fatigue:   ████░░░░░░  38/100                   │
│          │  Radiation: ███░░░░░░░  228/620 mSv              │
│          ├──────────────────────────────────────────────────┤
│          │  SKILLE: NAUKA 7 | DOWODZENIE 5 | PRZETRWANIE 5 │
│          │  GŁOSY: D:5 E:4 N:7 P:5 PA:6 S:3               │
│          │  STATUS: AKTYWNY | TRAIT: Architekt misji        │
├──────────┼──────────────────────────────────────────────────┤
│  [Mira]  │  ...                                             │
│  [Grzech]│  torpor | dzień 23/90                           │
│  [Yuki]  │  ...                                             │
│  [Amara] │  torpor | dzień 67/90                           │
│  [Lena]  │  torpor | dzień 12/90                           │
│  [Felix] │  torpor | dzień 45/90                           │
└──────────┴──────────────────────────────────────────────────┘
```

**Interakcje:**
- Klik na postać → ekspansja z pełnym profilem
- Klik na aktywną postać → opcje dialogu (jeśli `Captain's Rounds` dostępne)
- Klik na postać w torpor → szczegóły kapsuły i szansa wybudzenia
- Ikonki relacji (sojusz/neutralna/napięcie) obok każdej postaci

**Kolory statusów:**
- Aktywny: zielona ramka portretu
- Torpor: niebieska, przyciemniona
- Ranny (<60 Health): żółta
- Krytyczny (<35 Health): czerwona pulsująca

**Przejście:**
→ `BridgeScene` (przycisk powrotu)

---

### SystemsScene *(Systemy Statku)*

**Zadanie:** Status i zarządzanie systemami statku.

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│  SYSTEMY KAIROS                          [← MOSTEK]         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│     [Schemat statku — pixel cross-section]                  │
│                                                             │
│     Każdy system to klikalny moduł na schemacie.           │
│     Klik → panel szczegółów po prawej.                     │
│                                                             │
├──────────────────────────┬──────────────────────────────────┤
│  LISTA SYSTEMÓW          │  SZCZEGÓŁY (wybrany system)      │
│                          │                                  │
│  ○ Kadłub       89% ████ │  SENSORY                        │
│  ● Sensory      71% ███░ │  Sprawność: 71%                 │
│  ○ Lab          88% ████ │  Degradacja: −0,8%/turę         │
│  ○ Comm         76% ████ │  Efekt niski: NAUKA Yuki −1     │
│  ○ Medbay       91% ████ │                                  │
│  ○ Torpor (avg) 84% ████ │  [KONSERWACJA] koszt: 0 CZĘŚCI  │
│  ○ Warsztat     82% ████ │  [NAPRAWA +15%] koszt: 7 CZĘŚCI │
│  — ECLSS →             │  Check: INŻYNIERIA diff. 9        │
│                          │                                  │
│  ECLSS:                  │  Przydziel: [FELIX] lub [LENA]  │
│  ○ CO₂ Skruber  71% ███░ │                                  │
│  ○ Sabatier     95% ████ │  Uwaga: naprawa zajmuje slot    │
│  ○ WRS          88% ████ │  zadania przydzielonej osoby    │
│  ○ Hydroponika  79% ████ │                                  │
│  ○ Bioreaktory  91% ████ │                                  │
│  ○ Reaktor Fuz. 97% ████ │                                  │
└──────────────────────────┴──────────────────────────────────┘
```

**Interakcje:**
- Klik na system → panel szczegółów
- Klik `KONSERWACJA` / `NAPRAWA` → dodaje do kolejki przydziału
  *(gracz wróci do BridgeScene i zatwierdzi przydział)*
- Hover/tap na pasek zdrowia → tooltip z efektem niskiego poziomu

**Kolory systemu:**
- >75%: zielony
- 50–74%: żółty
- 25–49%: pomarańczowy
- <25%: czerwony pulsujący

**Przejście:**
→ `BridgeScene` (powrót)

---

### TorporScene *(Torpor — przejście między turami)*

**Zadanie:** Wizualizacja przejścia torporu. Upływ czasu. Zmiana aktywnej załogi.

**To jest moment ciszy między turami.**

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│                [ANIMACJA KAPSUŁ TORPORU]                    │
│                                                             │
│   Pikselowe kapsuły. Powoli zamykają się lub otwierają.    │
│   Bardzo wolna animacja — 2–3 sekundy.                     │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   DZI. 1246 → DZI. 1336                                    │
│   +90 dni hibernacji                                        │
│                                                             │
│   Promieniowanie (hibernowani): +16 mSv każdy              │
│   Promieniowanie (aktywni): +54 mSv każdy                  │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   „Nikt nie śnił. Przynajmniej nikt nie pamięta snów."     │
│                          — ARIA                             │
│                                                             │
│                    [KONTYNUUJ →]                            │
└─────────────────────────────────────────────────────────────┘
```

**Narracyjny fragment:** krótki, 1–2 zdania. Zmienia się co turę.
Pool ~20 fragmentów — ARIA, Jakub, lub postać która właśnie wychodzi/wchodzi.

**Dźwięk:** cichy. Hum sensorów. Ewentualnie jeden niski ton.
Nic dramatycznego — to rutyna. Po pięćdziesięciu latach.

**Przejście:**
→ `BridgeScene` (Faza 1 nowej tury)

---

### MapScene *(Mapa Misji)*

**Zadanie:** Wizualizacja trajektorii, postępu misji, opóźnienia sygnału.

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│  MAPA MISJI                              [← MOSTEK]         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ZIEMIA ●────────────────────────●·····················● LIMES│
│              Kairos ▲                                       │
│                                                             │
│  Postęp:    23%     ████████████░░░░░░░░░░░░░░░░░░░░░░░   │
│  Odległość od Ziemi:  1,61 ly                              │
│  Odległość do Limes: 12,59 ly                              │
│  Opóźnienie sygnału: 584 dni (→ Ziemia)                    │
│  Szacowany czas do Limes: 44 lata 8 mies.                 │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  HISTORIA SYGNAŁÓW:                                         │
│                                                             │
│  ▷ Tura 12: Sygnał osobisty → Paweł Nowak (oczekiwanie)   │
│  ▷ Tura 19: Raport WABK (nadano)                           │
│  ▷ Tura 28: Wiadomość z Ziemi (opóźn. 301 dni) [CZYTA]    │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  AKT II — DŁUGA CIEMNOŚĆ                                   │
│  Następny wymagany event: Third Quarter (Akt III, ~tura 87) │
└─────────────────────────────────────────────────────────────┘
```

**Interakcje:**
- Klik na wiadomość w historii → pełny tekst wiadomości
- Klik na punkt trajektorii → info o tym momencie misji
- Informacja o nadchodzącym forced event (aktowy, nie spoilerujący)

**Przejście:**
→ `BridgeScene` (powrót)

---

### LogbookScene *(Dziennik Kapitana)*

**Zadanie:** Historia decyzji, wpisy dziennika, narracja przebytej drogi.

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│  DZIENNIK KAPITANA                       [← MOSTEK]         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  TURA 38 | DZ. 1246 | AKT II                               │
│  ─────────────────────────────────────────                  │
│  > Grzech potrzebuje mniejszej ekspozycji.                  │
│    Amara to potwierdziła. Zmieniłem harmonogram.            │
│    On przyjął to bez słowa. Nie jestem pewien               │
│    co to znaczy.                                            │
│                                                             │
│  TURA 35 | DZ. 1126 | AKT II                               │
│  ─────────────────────────────────────────                  │
│  > Sensor widmo. 1420 MHz przez 4 minuty.                   │
│    Yuki oddychała za mną przez całe zdarzenie.              │
│    Powiedziałem: sprawdzamy sprzęt.                         │
│    Grzech nie znalazł usterki.                              │
│    Yuki to wie.                                             │
│                                                             │
│  [NOWY WPIS]                          [HISTORIA → PEŁNA]   │
└─────────────────────────────────────────────────────────────┘
```

**Zawartość logbooka:**
1. Automatyczne wpisy (po każdym evencie — 1–2 zdania z ARII)
2. Manualne wpisy kapitana (gracz pisze)
3. Wpisy o śmierciach postaci
4. Wpisy o przekroczeniu progów (Radiation, Third Quarter)

**Tryb read-only** (z MainMenu): gracz czyta historię ukończonej misji.

**Manualne wpisy:**
- Gracz pisze dowolny tekst (ograniczenie: 500 znaków)
- Wyzwala głos PAMIĘĆ (+arc point)
- Zostaje w logbooku permanentnie

**Przejście:**
→ `BridgeScene` (powrót)

---

## 6. SCENA SPECJALNA — AKT IV

---

### ApproachScene *(Zbliżenie do Limes)*

**Zadanie:** Widok podejścia do Limes. Protokoły biosygnatur. Interfejs naukowy.

**Dostępna tylko w Akcie IV gdy odległość do Limes <5 ly.**

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│  ZBLIŻENIE DO LIMES                      [← MOSTEK]         │
├─────────────────────────────────────────┬───────────────────┤
│                                         │  ODCZYTY          │
│   [Pixel art: planeta Limes rośnie]     │                   │
│   (mała na początku Aktu IV,            │  O₂: ░░░░░░░░    │
│    duża przy finałowych eventach)       │  CH₄: ░░░░░░░    │
│                                         │  H₂O: ░░░░░░░    │
│   Czerwony karzeł — tło                 │  DMS: ░░░░░░░    │
│   Atmosfera widoczna                    │                   │
│   Chmury (jeśli Lab + Sensory >70%)     │  [ANALIZA →]     │
│                                         │                   │
│                                         │  Sensory: 71%    │
│                                         │  Lab:     88%    │
│                                         │                   │
│                                         │  PROTOKOŁY:      │
│                                         │  ○ COSPAR: OFF   │
│                                         │  [AKTYWUJ]       │
├─────────────────────────────────────────┴───────────────────┤
│  YUKI: „Dane są czyste. Sprawdziłam sześć razy."            │
│  PROTOKÓŁ WERYFIKACJI: 0% ░░░░░░░░░░░░░░░░░░░░░░░          │
└─────────────────────────────────────────────────────────────┘
```

**Interakcje:**
- Pixel art planety ewoluuje z postępem protokołów
- Klik `AKTYWUJ COSPAR` → event `dms_confirmed` może być triggerowany tu
- Pasek postępu weryfikacji

**Przejście:**
→ `BridgeScene` (powrót / eventowanie)

---

## 7. SCENY KOŃCOWE

---

### EndingScene *(Zakończenie Narracyjne)*

**Zadanie:** Prezentacja jednego z sześciu zakończeń.
Ostatni logbook. Wskaźnik stanu misji.

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│                         [CZARNY]                            │
│                                                             │
│   Tekst logbooka pojawia się powoli.                        │
│   Jeden akapit. Pauza. Drugi akapit.                        │
│   Podpis: — J. Nowak / — ARIA                               │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   MISJA KAIROS — PODSUMOWANIE                               │
│   Czas misji: 38 lat 2 miesiące                             │
│   Załoga ocalała: 5/7                                       │
│   Odkrycie: TAK (DMS potwierdzone)                          │
│   Powrót: TAK                                               │
│   Stan statku przy zakończeniu: 67%                         │
│   Ostatni sygnał z Ziemi: 847 dni temu                     │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                [ZAPISZ LOGBOOK]    [NOWA MISJA]             │
└─────────────────────────────────────────────────────────────┘
```

**Dźwięk:** Dla zakończeń pozytywnych — delikatna muzyka.
Dla ZOSTAJĄ — cisza z jednym tonem.
Dla CISZA — dosłowna cisza.

---

### GameOverScene *(Koniec Katastroficzny)*

**Zadanie:** Prezentacja jednego z pięciu twardych końców gry (KG-01 do KG-05).

#### Layout

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│                         [CZARNY]                            │
│                                                             │
│   DEKOMPRESJA                                               │
│   MODUŁ GŁÓWNY                                              │
│   DZ. 1893                                                  │
│                                                             │
│   ARIA: Wszystkie systemy biologiczne: 0/7.                 │
│   ARIA: Kontynuuję monitoring statku.                       │
│   ARIA: Nadaję sygnał pozycyjny.                            │
│   ARIA: Czekam.                                             │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│   Tura: 47 | Akt: II | Ukończono: 27%                      │
│   Przyczyna: Kadłub — dekompresja                           │
├─────────────────────────────────────────────────────────────┤
│           [ZAPISZ LOGBOOK]    [NOWA MISJA]                  │
└─────────────────────────────────────────────────────────────┘
```

**Dźwięk:** Brak muzyki. Ewentualnie pojedynczy, głęboki ton na wejściu.

---

## 8. STUB — BattleScene

```typescript
// src/scenes/BattleScene.ts
export class BattleScene extends Phaser.Scene {
  constructor() {
    super({ key: 'Battle' });
  }

  create(): void {
    // TODO: pending mechanika/ — implementacja walki
    // Ta scena jest zarezerwowana i nie powinna być wywoływana w MVP.
    console.warn('BattleScene: not implemented, pending mechanika/');
    this.scene.start('Bridge');
  }
}
```

---

## 9. UI OVERLAYE — ARCHITEKTURA

Overlaye to HTML/CSS nad canvasem Phaser. Nie są scenami.
Lokalizacja: `src/ui/`

| Overlay | Plik | Kiedy widoczny |
|---|---|---|
| `ResourcePanel` | `ResourcePanel.ts` | BridgeScene zawsze |
| `CrewStatusBar` | `CrewStatusBar.ts` | BridgeScene zawsze |
| `ARIADialogue` | `ARIADialogue.ts` | BridgeScene + EventScene |
| `InnerVoicePanel` | `InnerVoicePanel.ts` | EventScene (gdy skill ≥ 4) |
| `TaskAssignModal` | `TaskAssignModal.ts` | BridgeScene (on demand) |
| `NotificationToast` | `NotificationToast.ts` | Globalny (progi alarmowe) |
| `TorturTransition` | `TorporOverlay.ts` | TorporScene |

**Zasada:** Overlaye słuchają eventów z `GameState.events`.
Nie mają własnej logiki — tylko rendering.

**Mobile touch targets:** minimum 48×48dp dla każdego interaktywnego elementu.

---

## 10. TEKST INTRO — WERSJA 1.0

*(Wyświetlany przed Turą 0, po przejściu z MainMenuScene)*

```
MISJA KAIROS
DZIEŃ 1 PODRÓŻY
ODLEGŁOŚĆ OD ZIEMI: 0,003 JEDNOSTKI ASTRONOMICZNE

Ziemia jest jeszcze widoczna przez iluminator.
Mały dysk. Niebieski.

Wiedziałeś że będzie wyglądać tak mała.
Wiedziałeś to od lat.

Mimo to — nie wiedziałeś.

> ARIA: Dobry ranek, Komandorze Nowak.
> Systemy nominalne. Załoga aktywna 7/7.
> Kurs: Limes, sektor 14H-HERALD.
> Szacowany czas podróży: 58 lat, 4 miesiące, 11 dni.
>
> Kiedy chce pan zacząć odprawę?

[TAK, zacznijmy]
```

*(Tekst zgodny z `docs/FABULA.md` — sekcja 8)*

---

## Screens update — v1.0

**Ukończono:**
- 14 scen MVP z opisami, layoutami i specyfikacją przepływu
- Diagram przepływu między scenami
- Stub `BattleScene` gotowy do implementacji
- Architektura UI overlayów
- Tekst intro Tury 0
- Layouty desktop i mobile dla `BridgeScene`
- Specyfikacja EventScene z mechaniką głosów wewnętrznych
