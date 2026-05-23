# 01 — Game Flow
## Pętla Rozgrywki | Wersja 1.0

> Ten plik definiuje główną pętlę gry: co się dzieje per tura, jak działa
> przydział zadań, jak działa torpor, jak przechodzą akty.
> Mechaniki zdarzeń → `mechanika/07-events.md`
> Mechaniki zasobów → `mechanika/03-resources.md`
> Mechaniki postaci → `mechanika/04-crew.md`
> Ostatnia aktualizacja: 2026-05

---

## FILOZOFIA PĘTLI

Ta gra nie jest grą o reagowaniu na kryzysy.
Jest grą o zarządzaniu entropią.

Czas działa przeciwko graczowi nie przez pojedyncze zdarzenia
— przez ciągłą, cichą degradację. Systemy się starzeją.
Leki się kończą. Załoga akumuluje promieniowanie.
Odczynniki laboratoryjne zużywają się bezpowrotnie.

Gracz który reaguje tylko na kryzysy przegrywa powoli.
Gracz który planuje — ma szansę.

**Każda tura jest decyzją o tym czego nie zrobisz.**
Masz ograniczoną aktywną załogę. Nie możesz naprawić wszystkiego,
zbadać wszystkiego i jednocześnie porozmawiać z Yuki.
To jest serce mechaniki.

---

## 1. JEDNOSTKA CZASU — TURA

```
1 TURA = 1 CYKL ROTACYJNY = ~4 miesiące misji

┌─────────────────────┬─────────────────────────────┐
│  OKRES AKTYWNY      │      TORPOR                 │
│  30 dni             │      90 dni                 │
│  (rozgrywka gracza) │   (czas przeskoczony)       │
└─────────────────────┴─────────────────────────────┘
```

**58 lat misji = ~174 tury łącznie**
*(174 × ~4 miesiące = ~696 miesięcy = ~58 lat)*

Gracz gra tylko w OKRESIE AKTYWNYM — te 30 dni per tura.
TORPOR jest pominięty mechanicznie, ale jego efekty są naliczane
(Radiation, Health degradacja, Fatigue reset).

---

## 2. PIĘĆ FAZ AKTYWNEGO OKRESU

Każda tura w okresie aktywnym przebiega przez pięć faz w stałej kolejności.

```
TURA N

  FAZA 1         FAZA 2         FAZA 3         FAZA 4         FAZA 5
  PRZEBUDZENIE → PRZYDZIAŁ  →   ZDARZENIE  →   ROZLICZENIE → TORPOR
  (stan statku)  (zadania)     (event/brak)    (efekty)      (koniec tury)
```

---

### FAZA 1 — PRZEBUDZENIE *(Awakening)*

Aktywna załoga budzi się z torporu lub kontynuuje aktywność.
ARIA przedstawia poranny raport.

**Co się dzieje:**
1. Ekran: Mostek (Bridge) — główny hub gry
2. ARIA: raport statusu systemów (anomalie, progi alarmowe)
3. Gracz widzi: kto jest aktywny, kto w torpor, stan zasobów i systemów
4. Jeśli to pierwsza tura po torpor: krótki moment dezorientacji narracyjnej
   *(„Spałeś 90 dni. Yuki jest aktywna od wczoraj.")*

**ARIA w fazie przebudzenia:**
> *„Dobry ranek, Komandorze. Systemy nominalne z wyjątkiem:
> CO₂ Scrubber: 71% (−3% od ostatniej aktywności).
> Dr Tanaka jest aktywna od 09:00. Dr Grzegorzewski: torpor, dzień 47/90.
> Misja: [X]% ukończona. Akt: [II/III/IV]."*

**Autosave:** ← po raporcie ARIA

---

### FAZA 2 — PRZYDZIAŁ ZADAŃ *(Task Assignment)*

Kapitan przydziela aktywną załogę do zadań na najbliższe 30 dni.
To jest główna decyzja zarządcza każdej tury.

**Zasada przydziału:**
- Każda aktywna osoba (w tym kapitan) = 1 slot zadania per tura
- Przy standardowej rotacji: aktywni = kapitan + 1 inna osoba
- Kapitan może wybudzić kogoś z torporu (koszt: Health −8 wybudzonego)
- Kapitan nie może przydzielić zadania osobie w torpor

**Lista zadań dostępnych:**

#### KONSERWACJA *(Maintenance)*
*Zapobiega pasywnej degradacji jednego systemu na tę turę*
- Kto: Grzech (INŻYNIERIA); Felix (Sensory/Comm); Lena (Sensory nawigacyjne); Yuki (Lab)
- Efekt: wybrany system nie degraduje pasywnie tej tury
- Koszt Fatigue: +10
- Brak check — rutyna

#### NAPRAWA *(Repair)*
*Przywraca zdrowie uszkodzonego systemu*
- Kto: Grzech (wszystkie systemy); inni tylko do difficulty ≤ 6
- Efekt: INŻYNIERIA check → przywrócenie zdrowia systemu
- Koszt: CZĘŚCI (per tabela z 03-resources.md i 05-ship-systems.md) + Fatigue +20
- Może naprawić tylko 1 system per przydział

#### BADANIA NAUKOWE *(Science)*
*Gromadzi dane z obserwacji kosmicznych i akumuluje LifeData*
- Kto: Yuki (NAUKA); Jakub (NAUKA, mniej efektywny)
- Efekt: +LifeData per turę; możliwe małe odkrycia narracyjne
- Wymaga: Sensory >40% AND Lab >20%
- Koszt: Fatigue +10

#### OPIEKA MEDYCZNA *(Medical)*
*Amara leczy lub prowadzi sesje psychologiczne*
- Kto: wyłącznie Amara
- Efekt: gracz wybiera cel (jedna postać) → MEDYCYNA check
  - Sukces: Health +5–15 lub Morale +5–12 (zależnie od potrzeby)
- Koszt: Fatigue Amary +10
- Uwaga: Amara może wybrać SIEBIE jako cel (Medbay sprawny ≥ 40%)

#### KALIBRACJA *(Calibration)*
*Spowalnia dryft kalibracyjny sensorów i komunikacji*
- Kto: Felix (Sensory + Comm); Lena (Sensory nawigacyjne)
- Efekt: wybrany system nie traci sprawności przez dryft tej tury
- Koszt: Fatigue +5
- Brak check — rutyna

#### ODPOCZYNEK *(Rest)*
*Postać regeneruje Fatigue*
- Kto: dowolna aktywna postać
- Efekt: Fatigue −30
- Koszt: brak (ale traci slot zadania)

#### ROZMOWA Z ZAŁOGĄ *(Captain's Rounds)*
*Kapitan spędza czas z konkretną osobą*
- Kto: wyłącznie kapitan (Jakub)
- Efekt: wybrana postać Morale +5–8; możliwe relacja +1 (probabilistic)
- Koszt: Fatigue kapitana +5
- Efekt dodatkowy: odblokowuje opcje dialogowe w najbliższym evencie z tą osobą

**Autosave:** ← po zatwierdzeniu przydziału

---

### FAZA 3 — ZDARZENIE *(Event)*

Po przydziale zadań — losowanie eventu.

**Szansa na event per tura: 35%**
*(Eventy FORCED ignorują losowanie — pojawiają się gdy spełniony warunek)*

**Jeśli event losowy:**
1. System sprawdza warunki wejścia dla wszystkich WEIGHTED eventów
2. Wagi kwalifikujących się eventów są sumowane
3. Losowanie weighted random
4. Event zostaje przedstawiony graczowi

**Jeśli brak eventu (65% tur):**
- Krótki narracyjny fragment z ARIA lub monolog wewnętrzny kapitana
- Nie jest mechanicznie pusty — jest oddechem
- Czasem Grzech coś mówi przy kolacji. Czasem Yuki patrzy przez iluminator.

**Przebieg eventu:**
1. Ekran zdarzenia — tekst narracyjny
2. Głosy wewnętrzne kapitana (jeśli wartość ≥ 4)
3. Opcje wyboru (2–4 opcje; niebieska opcja jeśli warunki spełnione)
4. Gracz wybiera
5. Check (jeśli wymagany) → wynik
6. Tekst rezultatu
7. Efekty aplikowane

**Autosave:** ← po każdym zakończonym evencie

---

### FAZA 4 — ROZLICZENIE *(Resolution)*

Wszystkie efekty pasywne i aktywne są aplikowane na koniec tury.
Gracz widzi podsumowanie zmian.

**Kolejność aplikowania efektów:**

```
1. Efekty zadań (naprawa, konserwacja, etc.)
2. Efekty eventu (jeśli był)
3. Produkcja ECLSS (TLEN, WODA, ŻYWNOŚĆ)
4. Konsumpcja zasobów przez aktywną załogę
5. Pasywna degradacja systemów (−% sprawności)
6. Radiation dla aktywnej załogi (+1,81 mSv × 30 dni = +54 mSv)
7. Health degradacja (kości: −1,5 pkt; Radiation debuff jeśli >50%)
8. Fatigue aktualizacja
9. Morale pasywne (−2/turę aktywności)
10. Sprawdzenie progów alarmowych → ARIA informuje
11. Sprawdzenie warunków KG → jeśli spełnione: sekwencja końcowa
```

**ARIA w fazie rozliczenia:**
Informuje tylko gdy przekroczony próg alarmowy.
Nie komentuje każdej zmiany — tylko anomalie.

> *„Komandorze. CO₂ Scrubber: 49%. Próg alarmowy przekroczony.
> Degradacja pasywna +1%/turę przy obecnym stanie.
> Sugeruję konserwację w przyszłym cyklu."*

---

### FAZA 5 — TORPOR *(Torpor Transition)*

Aktywna załoga wchodzi w torpor. Następna aktywna rotacja budzi się.

**Sekwencja torporu:**
1. Ekran: kapituły torporu — wizualizacja kto zasypia
2. Torpor 90 dni — efekty naliczane:
   - Radiation dla hibernowanych: +16 mSv (95% redukcja)
   - Health degradacja: −4,5 pkt
   - Morale: −3 pkt po wybudzeniu (dezorientacja temporalna)
   - Fatigue: reset do 0
3. Krótki narracyjny fragment
   *(„90 dni. Nikt nie śnił. Przynajmniej nikt nie pamięta snów.")*
4. Nowa aktywna załoga: wybudzenie
5. Tura N+1 — FAZA 1

**Możliwe zdarzenia torporu (10% szans per kapsuła per tura):**
- Anomalia torporu → event `torpor_anomaly_yuki` lub wariacja
- Nieplanowane wybudzenie → patrz mechanika kapsuł w 05-ship-systems.md

**Autosave:** ← przed wejściem w torpor (koniec tury)

---

## 3. AKCJE SPECJALNE KAPITANA

Poza przydziałem zadań kapitan może wykonać dodatkowe akcje
które nie zajmują slotu zadaniowego (wykonywane w trakcie Fazy 2 lub 3).

### DZIENNIK *(Captain's Log)*
- Gracz może napisać wpis do logbooka
- Uruchamia monolog wewnętrzny z głosami (szczególnie PAMIĘĆ)
- Brak efektu mechanicznego; efekt narracyjny
- Wpis zostaje w Logbooku gracza permanentnie

### SYGNAŁ DO ZIEMI *(Earth Transmission)*
- Gracz redaguje wiadomość do WABK lub wiadomość osobistą
- Wymaga: Comm >20%
- PAMIĘĆ głos aktywny
- Wiadomość „dotrze" za X lat (opóźnienie sygnału) — event z Ziemi za X tur
- Bandwidth ograniczony (per Comm health)

### ROZMOWA Z ARIĄ *(ARIA Dialogue)*
- Gracz może w dowolnym momencie zapytać ARIĘ o stan misji
- ARIA odpowiada na pytania techniczne, statusy, historię decyzji
- Z czasem (Akt II–III): ARIA może pytać z siebie
- Wątek Felix/ARIA: opcjonalnie śledzony przez te rozmowy

### PRZEGLĄD MAPY *(Navigation Review)*
- Gracz widzi trajektorię misji, procent ukończenia, odległość od Limes
- Możliwa korekta kursu (koszt PALIWO −1, PILOTAŻ check difficulty 3)
- Z Leną aktywną: +1 do wszystkich nawigacyjnych checków

---

## 4. ROTACJA TORPORU — SZCZEGÓŁY

### Standardowa rotacja (domyślna)

```
TURA  1: Kapitan aktywny + Grzech aktywny
TURA  2: Kapitan aktywny + Mira aktywna
TURA  3: Kapitan aktywny + Yuki aktywna
TURA  4: Kapitan aktywny + Amara aktywna
TURA  5: Kapitan aktywny + Lena aktywna
TURA  6: Kapitan aktywny + Felix aktywny
TURA  7: Kapitan aktywny + Grzech aktywny
... (cykl się powtarza)
```

Kapitan jest aktywny każdą turę.
*(Domyślnie. Gracz może zdecydować żeby Jakub też szedł w torpor — patrz niżej.)*

### Torpor kapitana (opcjonalne)
Jakub może wejść w torpor razem z innymi.
- Tura bez kapitana: Mira przejmuje aktywność jako "acting commander"
- Gracz nie kontroluje tej tury aktywnie
- Na koniec: ARIA raport o co się stało (zdarzenia rozwiązane automatycznie przez Mirę)
- Efekt: kapitan Radiation i Health degradują wolniej
- Ryzyko: gracz traci kontrolę nad 1 turą; Mira podejmuje decyzje

### Wybudzenie awaryjne
Gracz może wybudzić kogoś wcześniej z torporu.
- Koszt: Health −8 dla wybudzonego (stres termiczny)
- Radiation: +12 mSv (dodatkowa ekspozycja)
- Fatigue: zaczyna od 40 (nie od 0 — dezorientacja)
- Uzasadnienie: crisis events (event `eclss_co2_failure` wymaga Grzecha)

### Blokada torporu
Gracz może ZABLOKOWAĆ kogoś od wchodzenia w torpor
(np. Amara potrzebna przez 2 kolejne aktywne okresy).
- Koszt: brak mechaniczny w tej turze
- Koszt akumulacyjny: postać zbiera Radiation × 4 szybciej;
  Health degraduje × 3 szybciej bez przerwy torporu
- Morale: −3/turę dodatkowe bez odpoczynku torporu

---

## 5. STRUKTURA AKTÓW

Akty zmieniają się automatycznie na podstawie procentu ukończenia misji.
Nie ma ręcznego przełączenia — gra sama wie kiedy Third Quarter się zaczyna.

```
AKT I    AKT II      AKT III        AKT IV    AKT V
0–10%   10–50%      50–75%         75–90%   90–100%

  ●────────●──────────●──────────────●──────────●
  Start    Rutyna     3. Kwartał     Przybycie  Koniec
```

### Zmiany mechaniczne per akt

**Akt I (Odlot, 0–10%):**
- ARIA: aktywna rola tutorialowa (tłumaczy mechaniki naturalnie)
- Opóźnienie sygnału Ziemia: minuty → dni (rośnie)
- Eventy: głównie Motyw 1 (ciało) i Motyw 2 (maszyny)
- Morale degradacja: standardowa (−2/turę)
- Tura 0: specjalna (intro, brak eventów)

**Akt II (Długa Ciemność, 10–50%):**
- ARIA: zmniejsza aktywność tutorialową, zaczyna obserwować
- Opóźnienie sygnału: tygodnie → miesiące
- Eventy: Motyw 2 (maszyny) i Motyw 4 (Ziemia)
- PAMIĘĆ kapitana: zaczyna rosnąć automatycznie (+1 per akt)
- System degradacji: wyraźnie widoczne po 20+ turach

**Akt III (Trzeci Kwartał, 50–75%):**
- FORCED event: `last_dinner` (trigger gdy Morale dowolnej postaci <45)
- Morale degradacja: +50% (Third Quarter Phenomenon)
- Eventy: Motyw 3 (Trzeci Kwartał) dominuje
- Opóźnienie sygnału: lata
- SYGNAŁ głos: zaczyna mówić częściej niezależnie od wartości
- Szansa na event: 45% per tura (wzrost z 35%)

**Akt IV (Przybycie, 75–90%):**
- FORCED event: `first_signal_limes` (gdy odległość <3 ly)
- Tryb Zbliżenia: nowe akcje dostępne (approach protocols)
- Lab i Sensory: krytyczne dla odkrycia
- Szansa na event: 40% per tura
- Eventy: Motyw 5 (biosygnatury) dominuje

**Akt V (Rozwiązanie, 90–100%):**
- Decyzje kończące grę
- Powrót lub zostanie
- Logbook finale
- FORCED: zakończenie narracyjne

---

## 6. AKT IV — TRYB ZBLIŻENIA

Gdy misja wchodzi w Akt IV i odległość do Limes <5 lat świetlnych:
dodatkowe akcje przydziału stają się dostępne.

**Nowe zadania w Akcie IV:**

#### OBSERWACJA DALEKIEGO ZASIĘGU *(Long-Range Sensing)*
- Kto: Yuki + Felix (wspólnie; zajmuje oboje ich sloty)
- Efekt: +LifeData ×2; możliwy event `first_signal_limes` wcześniej
- Wymaga: Sensory >60%

#### PROTOKÓŁ ZBLIŻENIOWY *(Approach Protocol)*
- Kto: Lena + Jakub (razem)
- Efekt: przygotowanie trajektorii orbitalnej; PALIWO oszczędzony −1 na deceleration
- Wymaga: PILOTAŻ check difficulty 6

#### KWARANTANNA LABORATORYJNA *(Lab Quarantine Prep)*
- Kto: Amara + Yuki
- Efekt: Lab przygotowany na COSPAR protocols; +10% efektywności dla `dms_confirmed`
- Wymaga: Medbay >40% AND Lab >50%

---

## 7. TURA 0 — POCZĄTEK MISJI

Specjalna pierwsza tura. Jedyna bez możliwości eventu losowego.

**Sekwencja:**
1. Ekran czarny → tekst intro (z `docs/FABULA.md`)
2. Mostek pojawia się — `Kairos` w ruchu
3. ARIA: pierwsze przywitanie i raport
4. Gracz: przegląd stanu statku (tutorial ARIA)
5. Przydział Tury 0: gracz dostaje pełną załogę aktywną
   *(pierwszy i jedyny raz gdy wszyscy są jednocześnie aktywni)*
6. Brak eventu — tylko narracja
7. Krótka scena: kolacja pierwszego dnia
8. Torpor — wszyscy oprócz kapitana i Grzecha wchodzą w torpor
9. Tura 1 — normalna pętla

**Cel Tury 0:**
Przedstawić wszystkich. Pokazać jak wygląda "normalny" dzień.
Zanim normalność zniknie.

---

## 8. MOSTEK — CENTRUM NAWIGACYJNE

Mostek to główny ekran gry. Wszystkie decyzje zarządcze zaczynają się tu.

**Elementy interfejsu Mostku:**

```
┌─────────────────────────────────────────────────────┐
│  KAIROS | AKT [II] | [X]% MISJI | TURA [N]         │
├──────────────┬──────────────────┬───────────────────┤
│  ZASOBY      │  SYSTEMY         │  ZAŁOGA           │
│  ○ TLEN: 74  │  ○ Kadłub: 89%  │  Jakub: aktywny   │
│  ○ WODA: 63  │  ○ Sensory: 71% │  Grzech: aktywny  │
│  ○ ŻYWNOŚĆ:  │  ○ Lab: 88%     │  Yuki: torpor 23d │
│    48        │  ○ Comm: 76%    │  Mira: torpor 67d │
│  ○ PALIWO:87 │  ○ Medbay: 91%  │  Amara: torpor 12d│
│  ○ CZĘŚCI:61 │  ○ Warsztat: 82%│  Lena: torpor 89d │
│              │  ○ ECLSS: [tab] │  Felix: torpor 34d│
├──────────────┴──────────────────┴───────────────────┤
│  ARIA: "CO₂ Scrubber: 71%. Sugeruję konserwację."  │
├─────────────────────────────────────────────────────┤
│  [PRZYDZIAŁ ZADAŃ]  [DZIENNIK]  [SYGNAŁ DO ZIEMI]  │
│  [ROZMOWA Z ARIĄ]   [MAPA MISJI]                    │
└─────────────────────────────────────────────────────┘
```

Retro-pixel estetyka — terminal lat 80. z 2099 roku.
Interfejs zaprojektowany przez ludzi którzy myśleli że retro jest wiarygodne.

---

## 9. AUTOSAVE — KOMPLETNA LISTA

| Moment | Punkt autozapisu |
|---|---|
| Po raporcie ARIA (Faza 1) | ✓ |
| Po zatwierdzeniu przydziału (Faza 2) | ✓ |
| Po każdym zakończonym evencie (Faza 3) | ✓ |
| Po rozliczeniu tury (Faza 4) | ✓ |
| Przed wejściem w torpor (Faza 5) | ✓ |
| Po śmierci postaci (zawsze) | ✓ |
| Po każdym wymuszonym wybudzeniu z torporu | ✓ |
| Przed każdym przejściem aktowym | ✓ |

**Implementacja:** Dexie.js (IndexedDB) — `src/storage/SaveSystem.ts`
Jeden aktywny slot + automatyczna kopia zapasowa (poprzedni punkt).
Gracz nie może manualnie ładować zapisów — permadeath.

---

## 10. DIAGRAM PEŁNEJ PĘTLI

```
     ┌─────────────────────────────────────────────┐
     │                  NOWA GRA                   │
     │              Tura 0 (specjalna)             │
     └─────────────────────┬───────────────────────┘
                           │
                           ▼
     ┌─────────────────────────────────────────────┐
     │           FAZA 1: PRZEBUDZENIE              │
     │         ARIA raport | Stan statku           │
     │              [AUTOSAVE]                     │
     └─────────────────────┬───────────────────────┘
                           │
                           ▼
     ┌─────────────────────────────────────────────┐
     │        FAZA 2: PRZYDZIAŁ ZADAŃ              │
     │    Konserwacja / Naprawa / Badania /        │
     │    Opieka / Kalibracja / Odpoczynek /       │
     │    Rozmowa z załogą                         │
     │    + Akcje specjalne kapitana               │
     │              [AUTOSAVE]                     │
     └─────────────────────┬───────────────────────┘
                           │
                ┌──────────▼──────────┐
                │  Losowanie eventu   │
                │    35% szans        │
                └──────┬──────┬───────┘
                       │      │
              EVENT    │      │  BRAK EVENTU
                       ▼      ▼
     ┌──────────────────┐  ┌──────────────────────┐
     │ FAZA 3: ZDARZENIE│  │  Narracyjny fragment │
     │ Tekst + głosy    │  │  (Grzech, Yuki,      │
     │ Wybór + check    │  │   ARIA, cisza)       │
     │ Rezultat         │  │                      │
     │    [AUTOSAVE]    │  │                      │
     └──────────┬───────┘  └──────────┬───────────┘
                └──────────┬──────────┘
                           │
                           ▼
     ┌─────────────────────────────────────────────┐
     │          FAZA 4: ROZLICZENIE                │
     │  Zasoby | Systemy | Parametry załogi        │
     │  Progi alarmowe | Warunki KG                │
     └─────────┬───────────────────────────┬───────┘
               │                           │
        ┌──────▼──────┐          ┌─────────▼──────────┐
        │  NORMALNIE  │          │  WARUNEK KG         │
        │             │          │  SPEŁNIONY          │
        │             │          │  → Sekwencja końca  │
        └──────┬──────┘          └────────────────────┘
               │
               ▼
     ┌─────────────────────────────────────────────┐
     │           FAZA 5: TORPOR                   │
     │  Zmiana aktywnej załogi | Efekty hibernacji │
     │  90 dni → [AUTOSAVE] → Tura N+1            │
     └─────────────────────┬───────────────────────┘
                           │
                           ▼
                    ┌──────────────┐
                    │  Przejście   │
                    │  aktowe?     │
                    └──────┬───────┘
                     TAK   │  NIE
              ┌────────────┤
              ▼            ▼
     ┌─────────────┐   ┌────────────────────┐
     │  NOWY AKT   │   │  Powrót do Fazy 1  │
     │  (zmiany    │   │  Tura N+1          │
     │  mechaniczne│   └────────────────────┘
     │  + narracja)│
     └──────┬──────┘
            ▼
     Powrót do Fazy 1
```

---

## 11. TEMPO I PACING

Gra nie ma timera ani presji czasowej w tradycyjnym sensie.
Ale ma *presję entropii* — im dłużej trwa misja, tym więcej degraduje.

**Typowy czas sesji:**
Jedna sesja = 3–8 tur (około 1–2 godziny grania)
Pełna kampania: 174 tury (wiele sesji)
Nie ma potrzeby kończenia w jednej sesji — logbook i autosave przechowują stan.

**Pacing per akt:**
- Akt I: wolny, tutorial tempo, budowanie świata
- Akt II: rutyna z narastającą entropią — gracz się uczy priorytetyzacji
- Akt III: najwyższe tempo eventów, najtrudniejsze decyzje, Third Quarter
- Akt IV: ekscytacja odkrycia kontra kruchość zasobów po 40+ turach
- Akt V: emocjonalny finał — mechanicznie uproszczony, narracyjnie najgęstszy

---

## Game Flow update — v1.0

**Ukończono:**
- Pięciofazowa tura z pełnymi opisami faz
- System przydziału zadań (7 typów zadań)
- Akcje specjalne kapitana
- Mechanika rotacji torporu (standardowa, opcjonalna, awaryjna)
- Struktury aktów z zmianami mechanicznymi
- Tryb zbliżenia (Akt IV)
- Tura 0 (specjalna sekwencja startowa)
- Diagram pełnej pętli
- Mapa autosave
- Schemat interfejsu Mostku
