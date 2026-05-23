# 06 — Missions
## Typy Misji | Wersja 1.0

> Misje to akcje które gracz INICJUJE przez przydział zadań.
> Różnią się od eventów: eventy dzieją się graczowi, misje gracz wybiera.
> Misje podróżne: dostępne przez całą grę.
> Misje Limes: odblokowywane w Akcie IV.
> Ostatnia aktualizacja: 2026-05

---

## FILOZOFIA MISJI

Misja to nie quest z nagrodą.
Misja to decyzja o tym jak spędzasz ograniczony czas aktywny.

Każda misja zajmuje slot zadania osoby która ją wykonuje.
Przez turę w której Yuki prowadzi spektroskopię długiego zasięgu —
Yuki nie może być z Amarą, nie może pomagać przy naprawie Lab,
nie może odpocząć.

**Misja i event mogą kolidować:**
Jeśli event wymaga Yuki podczas jej dwuturowej misji powierzchniowej —
coś musi ustąpić. To jest napięcie które gra chce wywoływać.

---

## KATEGORIE MISJI

```
MISJE PODRÓŻNE          MISJE LIMES
(Akty I–IV)             (Akt IV–V)
│                        │
├── Konserwacja           ├── ORBITALNE
├── Naprawa               │   ├── Skanowanie atmosferyczne
├── Obserwacja naukowa    │   └── Mapowanie powierzchni
├── Opieka medyczna       │
├── Kalibracja            └── POWIERZCHNIOWE (high stakes)
└── Transmisja                ├── Ekspedycja atmosferyczna
                              ├── Protokół COSPAR
    MISJE PODEJŚCIA           └── Analiza próbek biologicznych
    (Akt IV, <5 ly)
    ├── Spektroskopia dalekiego zasięgu
    ├── Protokół orbitalny
    └── Przygotowanie laboratorium
```

---

## SCHEMAT OPISU MISJI

Każda misja opisana według schematu:

```
ID: snake_case
Typ: journey / approach / orbital / surface
Dostępna: akty / warunki
Kto: główna postać + opcjonalnie wsparcie
Wymaga: systemy, zasoby, stan postaci
Tura: ile tur trwa
Koszt: Fatigue, CZĘŚCI, PALIWO itd.
Check: skill / difficulty / opcjonalność
Sukces: efekty
Porażka: efekty
Katastrofa: przy wyniku ≤ difficulty −3
Narracja: klimatyczne zdanie
```

---

## 1. MISJE PODRÓŻNE *(zawsze dostępne, Akty I–IV)*

---

### M01: PRZEGLĄD SYSTEMU *(System Review)*

```
ID:        system_review
Typ:       journey
Dostępna:  zawsze
Kto:       Grzech (INŻYNIERIA); Felix (Sensory/Comm); Lena (Sensory nawig.); Yuki (Lab)
Tura:      1
Koszt:     Fatigue +10
Check:     brak (rutyna)
```

**Opis:** Planowy przegląd jednego systemu. Grzech, Felix, Lena lub Yuki
poświęcają aktywny okres na utrzymanie wybranego systemu w dobrym stanie.

**Efekt sukcesu:**
Wybrany system nie traci sprawności pasywnej w tej turze.
*(Zatrzymuje degradację, nie naprawia istniejących uszkodzeń.)*

**Wybór systemu per postać:**

| Postać | Dostępne systemy |
|---|---|
| Grzech | wszystkie |
| Felix | Sensory, Comm |
| Lena | Sensory (nawigacyjne) |
| Yuki | Lab, Hydroponika |
| Amara | Medbay, Torpor Chambers |

> *„Maszyny mówią ci kiedy potrzebują uwagi.
> Problem polega na tym że mówią ci dopiero gdy jest już późno."*
> — Grzech.

---

### M02: NAPRAWA AWARYJNA *(Emergency Repair)*

```
ID:        emergency_repair
Typ:       journey
Dostępna:  gdy dowolny system <80%
Kto:       Grzech (główny); inni tylko difficulty ≤ 6
Tura:      1
Koszt:     CZĘŚCI (per tabela 05-ship-systems.md) + Fatigue +20
Check:     INŻYNIERIA vs difficulty (per system)
```

**Opis:** Aktywna naprawa uszkodzonego systemu. Różni się od M01:
M01 zapobiega, M02 przywraca.

**Efekt sukcesu (pełny):** System +10–35% sprawności
*(zależnie od trudności i dostępnych CZĘŚCI)*

**Efekt sukcesu (z komplikacją):** System +5–15%; jeden dodatkowy koszt
*(Fatigue +10 lub CZĘŚCI +2)*

**Efekt porażki:** System bez zmiany; CZĘŚCI stracone na próbę (50%)

**Efekt katastrofy:** System −5%; CZĘŚCI stracone; Grzech Fatigue +20

**Specjalna zasada:** Trait Grzecha *Śląski sposób* zmienia Porażkę
w Częściowy sukces. Katastrofa pozostaje katastrofą.

> *„Naprawiasz naprawy napraw. Po dwudziestu latach w polu
> nie rozróżniasz już maszyny od jej historii."*
> — Grzech, tura 47.

---

### M03: OBSERWACJA KOSMICZNA *(Space Observation)*

```
ID:        space_observation
Typ:       journey
Dostępna:  zawsze
Kto:       Yuki (NAUKA 9, główna); Jakub (NAUKA 7, mniej efektywny)
Wymaga:    Sensory >50% AND Lab >40%
Tura:      1
Koszt:     Fatigue +10
Check:     NAUKA vs difficulty 6
```

**Opis:** Yuki lub Jakub gromadzi dane naukowe z trwającej podróży —
spektroskopia tła, obserwacje układów mijanych, analiza promieniowania.
Chleb powszedni misji naukowej.

**Efekt sukcesu (pełny):** LifeData +2; możliwe małe odkrycie narracyjne
*(5% szans na krótki event naukowy bez wyboru — just flavor)*

**Efekt sukcesu (z komplikacją):** LifeData +1

**Efekt porażki:** LifeData +0; Yuki Morale −2
*(Zmarnowany dzień badań. Ona wie.)*

**Modyfikator Yuki vs Jakub:**
- Yuki (NAUKA 9): efektywność ×1,5
- Jakub (NAUKA 7): efektywność ×1,0
- Przy Sensory <65%: efektywność ×0,7

> *„Dane płyną przez cały czas. Pytanie brzmi
> czy masz oczy żeby je czytać."*
> — Dr Yuki Tanaka.

---

### M04: SESJA MEDYCZNA *(Medical Session)*

```
ID:        medical_session
Typ:       journey
Dostępna:  zawsze (jeśli Amara aktywna)
Kto:       wyłącznie Amara (MEDYCYNA 9)
Wymaga:    Medbay >20%
Tura:      1
Koszt:     Fatigue Amary +10
Check:     MEDYCYNA vs difficulty 6
```

**Opis:** Amara poświęca aktywny okres jednej osobie —
leczenie fizyczne lub sesja psychologiczna.
Gracz wybiera cel i typ sesji.

**Typy sesji:**

| Typ | Efekt sukcesu | Wymaga |
|---|---|---|
| Leczenie fizyczne | Health celu +5–15 | — |
| Psychologiczna | Morale celu +5–12 | Medbay >40% |
| Badanie profilaktyczne | Ujawnia ukryty stan zdrowia / Radiation celu | — |
| Sesja własna | Amara Health +5 lub Morale +8 | Medbay >40% |

**Efekt porażki:** Health lub Morale celu +2 (przynajmniej coś)

**Trait Amary *Widzę cię*:** przy Badaniu profilaktycznym — automatycznie
ujawnia ukryty stan psychologiczny. Nie wymaga sprawdzenia.

**Ograniczenie:** Amara może przeprowadzić maksymalnie 1 sesję per tura.
Przy Fatigue >80: difficulty +2 dla wszystkich checków.

> *„Zna stan każdej osoby na statku lepiej niż ta osoba zna siebie."*
> — `docs/FABULA.md`

---

### M05: KALIBRACJA *(Calibration)*

```
ID:        calibration
Typ:       journey
Dostępna:  zawsze
Kto:       Felix (NAUKA 7, Sensory + Comm); Lena (PILOTAŻ 10, Sensory nawig.)
Tura:      1
Koszt:     Fatigue +5
Check:     brak (rutyna poniżej progów alarmowych)
```

**Opis:** Felix lub Lena utrzymuje precyzję systemów pomiarowych.
Felix robi to automatycznie jeśli jest aktywny — można to uznać za jego
"tło" per tura, ale jeśli gracz chce gwarancji: musi przydzielić slot.

**Efekt:** Wybrany system (Sensory lub Comm) nie traci sprawności
przez dryft kalibracyjny tej tury.

**Reguła Felix:** Jeśli Felix jest aktywny i nie ma przydzielonego innego zadania,
ARIA automatycznie przydziela mu Kalibrację Sensorów i Comm.
*(Nie wymaga akcji gracza — Felix po prostu to robi.)*

---

### M06: TRANSMISJA DO ZIEMI *(Earth Transmission)*

```
ID:        earth_transmission
Typ:       journey
Dostępna:  Comm >20%
Kto:       kapitan (Jakub) — decyzja co wysłać
Tura:      1
Koszt:     bandwidth (per Comm health + odległość)
Check:     brak
```

**Opis:** Jakub kompiluje i wysyła raport naukowy lub wiadomość osobistą.
Każda transmisja to decyzja o tym co jest ważne — bandwidth jest skończony.

**Typy transmisji:**

| Typ | Koszt bandwidth | Efekt |
|---|---|---|
| Raport naukowy | wysoki | LifeData wysłane; WABK "zadowolone" |
| Wiadomość osobista | niski | PAMIĘĆ arc point; możliwy event z odpowiedzią |
| Raport statusu | średni | Protokół spełniony |
| Transmisja odkrycia | bardzo wysoki | Aktywuje historyczny moment — Ziemia dowie się za 14 lat |

**Narracyjny efekt:** transmisje z Ziemi nadchodzą z opóźnieniem.
Każda wysłana wiadomość może wygenerować event odpowiedzi
za X tur (= X lat świetlnych opóźnienia / ~4 miesiące per tura).

---

## 2. MISJE PODEJŚCIA *(Akt IV, odległość <5 ly od Limes)*

---

### M07: SPEKTROSKOPIA DALEKIEGO ZASIĘGU

```
ID:        long_range_spectroscopy
Typ:       approach
Dostępna:  Akt IV AND odległość <5 ly
Kto:       Yuki + Felix (razem — zajmuje oba sloty)
Wymaga:    Sensory >60% AND Lab >50%
Tura:      1
Koszt:     Fatigue oboje +15
Check:     NAUKA Yuki difficulty 6
```

**Opis:** Yuki i Felix prowadzą intensywną spektroskopię — pełne pasmo,
wszystkie protokoły detekcji jednocześnie. To jest Yuki tuż przed tym
czego całe życie szukała.

**Efekt sukcesu (pełny):**
- LifeData +4 (podwójne wobec standardowej obserwacji)
- Szansa 30% na wczesny trigger eventu `first_signal_limes`
- Felix log: anomalia w danych (flag dla wątku Felix/ARIA)

**Efekt sukcesu (z komplikacją):**
- LifeData +2
- Dane niekompletne — wymagają dodatkowej tury dla `first_signal_limes`

**Efekt porażki:**
- LifeData +1
- Yuki Morale −5 (K2-18b nigdy nie jest daleko)

> *„Całe życie poczeka na ten moment. Teraz jest tu.
> I boi się."* — `docs/FABULA.md`

---

### M08: PROTOKÓŁ ORBITALNY

```
ID:        orbital_protocol
Typ:       approach
Dostępna:  Akt IV AND odległość <3 ly
Kto:       Lena + Jakub (razem)
Tura:      1
Koszt:     Fatigue oboje +10
Check:     PILOTAŻ Leny difficulty 6
```

**Opis:** Przygotowanie optymalnej trajektorii orbitalnej.
Lena liczy, Jakub zatwierdza. Przy deceleration burn —
każda zaoszczędzona jednostka paliwa jest decyzją o przyszłości.

**Efekt sukcesu (pełny):**
- PALIWO: −1 zaoszczędzone przy deceleration burn
- Deceleration difficulty: −1 (łatwiejszy manewr)
- Lena Morale: +5 (dobre lądowanie jest dla niej estetyczne)

**Efekt sukcesu (z komplikacją):**
- Tylko efekt Fatigue, bez oszczędności

**Efekt porażki:**
- Suboptymalna trajektoria: PALIWO +1 przy deceleration
- Lena Morale: −3

**Trait Leny *Czyste lądowanie*:** aktywny przy tym checku —
nawet porażka nie może dać kaskady.

---

### M09: PRZYGOTOWANIE LABORATORIUM

```
ID:        lab_preparation
Typ:       approach
Dostępna:  Akt IV AND odległość <4 ly
Kto:       Amara + Yuki (razem)
Wymaga:    Medbay >40% AND Lab >50%
Tura:      1
Koszt:     Fatigue oboje +10
Check:     MEDYCYNA Amary difficulty 6
```

**Opis:** Amara i Yuki razem przygotowują laboratorium na protokoły COSPAR.
Sterylizacja, weryfikacja containment, staging próbek.
To jest protokół który Yuki znała na pamięć od 2082.

**Efekt sukcesu (pełny):**
- Lab: +10% sprawności permanentnie dla misji Limes
- COSPAR lockdown czas: skrócony do 48h (zamiast 72h) jeśli protokół aktywny
- Yuki Morale: +8 (gotowość jest formą kontroli)

**Efekt porażki:**
- Lab bez zmiany
- COSPAR wymaga pełnych 72h

---

## 3. MISJE LIMES — ORBITALNE *(Akt IV, po osiągnięciu orbity)*

---

### M10: SKANOWANIE ATMOSFERYCZNE

```
ID:        atmospheric_scan
Typ:       orbital
Dostępna:  Akt IV AND w orbicie Limes
Kto:       Yuki (NAUKA 9, wymagana)
Wymaga:    Sensory >65% AND Lab >50%
Tura:      1
Koszt:     Fatigue Yuki +15
Check:     NAUKA difficulty 6
```

**Opis:** Pierwsze bezpośrednie skanowanie atmosfery Limes.
Spektroskopia absorpcyjna — każdy pik na wykresie to możliwa odpowiedź.
Yuki czyta dane w czasie rzeczywistym. Drżą jej ręce.

**Efekt sukcesu:** Triggeruje event `first_signal_limes` lub `false_biosignature`
*(zależnie od flag wcześniejszych decyzji i losowania — patrz 07-events.md)*

**Efekt porażki:** Dane niekompletne — wymagana dodatkowa tura skanowania.
LifeData +1. Yuki Morale −5.

**Ważna reguła:** Bez tej misji event `first_signal_limes` nie może wystąpić.
To gracz musi aktywnie zlecić skanowanie — odkrycie nie przyjdzie samo.

---

### M11: MAPOWANIE POWIERZCHNI

```
ID:        surface_mapping
Typ:       orbital
Dostępna:  Akt IV AND w orbicie
Kto:       Felix + opcjonalnie Yuki
Wymaga:    Sensory >50%
Tura:      1
Koszt:     Fatigue Felix +10
Check:     NAUKA difficulty 6
```

**Opis:** Felix koordynuje sensory w systematycznym skanowaniu powierzchni.
Temperatura, geologia, potencjalne strefy lądowania.
Dane trafiają na mapy Leny.

**Efekt sukcesu (pełny):**
- Identyfikacja 2–3 stref lądowania
- Misja M12 (Ekspedycja atmosferyczna): difficulty −1
- LifeData +2

**Efekt sukcesu (z komplikacją):**
- 1 strefa lądowania; LifeData +1

**Efekt porażki:**
- Brak rekomendacji lądowania; misja M12 bez modyfikatora

---

## 4. MISJE LIMES — POWIERZCHNIOWE *(Akt IV–V, wysokie stawki)*

Misje powierzchniowe są wieloturowe i nieprzerywalne bez kosztu.
Wymagają przydziału krytycznych specjalistów.
Wiążą się z realnym ryzykiem śmierci postaci.

---

### M12: EKSPEDYCJA ATMOSFERYCZNA

```
ID:        atmospheric_expedition
Typ:       surface
Dostępna:  po event `first_signal_limes` lub `dms_confirmed`
Kto:       Yuki (NAUKA, wymagana) + Lena (PILOTAŻ, wymagana)
Wymaga:    Sensory >60% AND Lab >60% AND PALIWO ≥ 50
Tura:      2 (misja wieloturowa — obie tury zablokowane)
Koszt:     PALIWO −3; CZĘŚCI −5; Fatigue oboje +25
Check:     PILOTAŻ Leny difficulty 9 → NAUKA Yuki difficulty 9 (sequential)
```

**Opis:** Lądownik wchodzi w atmosferę Limes. Lena pilotuje.
Yuki pobiera próbki. Dwie godziny w atmosferze planety
z prawdopodobnie żywymi organizmami.

**Mechanika wieloturowa:**

```
TURA 1: PILOTAŻ check — wejście atmosferyczne i lądowanie
  → Sukces pełny: lądowanie nominalne
  → Sukces z komplikacją: twarde lądowanie; CZĘŚCI −3 (uszkodzenie lądownika)
  → Porażka: abortuj; Yuki i Lena wracają; misja anulowana; PALIWO −2
  → Katastrofa: wypadek; Lena Health −30 lub Yuki Health −30

TURA 2: NAUKA check — pobieranie próbek
  → Sukces pełny: próbki zebrane; LifeData +8; triggeruje M13 (obowiązkowo)
  → Sukces z komplikacją: próbki częściowe; LifeData +4; M13 opcjonalne
  → Porażka: próbki skażone; LifeData +1; M13 niemożliwe
  → Katastrofa: kontaminacja lądownika; M13 przyspieszone; risk flag
```

**Po sukcesie:** COSPAR protokół OBOWIĄZKOWY przed analizą.
Yuki i Lena w kwarantannie — natychmiast aktywuje M13.

**Trait Leny *Czyste lądowanie*:** aktywny dla PILOTAŻ check w Turze 1.
Nawet przy Porażce: brak katastrofy dla lądownika.
Ale Yuki i tak może ucierpieć przy katastrofie NAUKI.

> *„Lena lubi kiedy statek drży przy zmianie kursu —
> bo to znaczy że jest prawdziwy."*
> — `docs/FABULA.md`

---

### M13: PROTOKÓŁ KWARANTANNY COSPAR

```
ID:        cospar_quarantine
Typ:       surface
Dostępna:  po M12 (obowiązkowo jeśli sukces pełny)
Kto:       Amara (główna) + Yuki (w kwarantannie)
Wymaga:    Medbay >40% AND Lab >60%
Tura:      2 (nieprzerywalne)
Koszt:     Fatigue Amary +15 per tura; brak CZĘŚCI
Check:     brak (proceduralne; standardowe) LUB MEDYCYNA difficulty 6
           jeśli skrócone do 48h (M09 wykonana wcześniej)
```

**Opis:** Protokół COSPAR Category IV.
72 godziny lockdown. Amara monitoruje Yuki i próbki.
Nikt nie wychodzi. Nikt nie wchodzi.

Yuki siedzi w laboratorium ze zbiornikami próbek
i czeka na potwierdzenie że nie przywiozła czegoś
czego nie powinna była.

**Mechanika wieloturowa:**

```
TURA 1–2: Kwarantanna
  → Yuki i Amara niedostępne dla innych zadań
  → Yuki Morale: −5/turę (izolacja + oczekiwanie)
  → Amara Morale: −3/turę

KONIEC TURY 2:
  → Check procedury: MEDYCYNA Amary (check tylko jeśli Medbay <60%)
  → Sukces: próbki czyste; przejście do M14
  → Porażka: ryzyko kontaminacji; dodatkowa tura kwarantanny
```

**Jeśli M09 wykonana wcześniej:** tylko 1 tura (48h skrócony protokół).

**Narracja:**
> *„Amara modli się. Cicho, prywatnie.*
> *Yuki nie pyta o co. Rozumie.*
> *72 godziny."*

---

### M14: ANALIZA PRÓBEK BIOLOGICZNYCH

```
ID:        biological_analysis
Typ:       surface
Dostępna:  po M13 (po zakończeniu kwarantanny)
Kto:       Yuki (NAUKA 9, wymagana) + Felix (wsparcie techniczne)
Wymaga:    Lab >60% AND oboje aktywni
Tura:      1
Koszt:     Fatigue oboje +20
Check:     NAUKA difficulty 12 (trudna — życie to skomplikowany obiekt)
```

**Opis:** Definitywna analiza. Sekwencjonowanie, mikroskopia, testy metaboliczne.
Yuki i Felix razem przez 30 godzin ciągłej pracy.

Po tej misji gra wie czy Limes ma życie.
Yuki wie czy miała rację.

**Efekt sukcesu (pełny):**
- Życie POTWIERDZONE — event `dms_confirmed` triggerowany z wynikiem pełnym
- LifeData +10
- Yuki Morale: +25 (ale to napięcie które rozwiązuje się jak płacz)
- Misja naukowa: 100% ukończona

**Efekt sukcesu (z komplikacją):**
- Życie MOŻLIWE — wnioski niejednoznaczne; potrzebna dodatkowa tura
- LifeData +5
- Yuki: „To jest coś. Nie wiem jeszcze co."

**Efekt porażki:**
- Wyniki negatywne lub nierozerwalnie skażone
- LifeData +2 (dane procesowe)
- Yuki Morale: −20
- Zakończenie CICHY POWRÓT lub PYRRUSOWE staje się bardziej prawdopodobne

**Efekt katastrofy (difficulty −3):**
- Wyniki sprzeczne — nigdy nie będzie pewności
- To jest naukowo najgorszy możliwy wynik
- Yuki: cisza. Przez kilka tur.

> *„Tym razem mam rację."*
> — Dr Yuki Tanaka, event `dms_confirmed`.

---

## 5. MECHANIKA MISJI WIELOTUROWYCH

### Zasady

**Blokowanie:** Postać przypisana do misji wieloturowej
nie może być przydzielona do innego zadania przez wszystkie tury misji.

**Przerwanie:** Gracz może przerwać misję wieloturową przed jej zakończeniem.
Koszt przerwania:
- Strata wszystkich dotychczasowych efektów
- Fatigue: +15 dodatkowe dla uczestników (stres)
- CZĘŚCI i PALIWO stracone (nie do odzyskania)
- Dla M13: przerwanie kwarantanny = risk flag (możliwy event kontaminacji)

**Kolizja z eventem:** Gdy event wymaga konkretnej postaci zaangażowanej w misję:
```
Opcja A: Przerwij misję (powyższe koszty) — postać dostępna dla eventu
Opcja B: Ignoruj event (misja kontynuowana) — event rozwiązany automatycznie
          przez najlepszą dostępną postać (nie przez gracza)
          Ryzyko: gorszy wynik eventu
```

**Torpor podczas misji:** Wieloturowe misje powierzchniowe
nie mogą być przerywane przez torpor. Postać pozostaje aktywna.
Radiation i Fatigue akumulują normalnie przez dodatkowe tury aktywności.

---

## 6. WSKAŹNIK POSTĘPU ODKRYCIA — LIFEDATA

LifeData to miara naukowego postępu misji.
Nie jest zasobem — jest akumulatorem.

```
LIFEDATA — skala 0–100

0──────┬──────────┬──────────┬──────────┬──────────100
       25         50         75         100
       │          │          │          │
   Pierwsze    Sygnatura   Próbki     Analiza
   dane       atmosfer.   zebrane    biologiczna
   z rejsu    z Limes                definitywna
```

**Progi narracyjne:**

| Próg | Efekt |
|---|---|
| 0–24 | Dane z rejsu; ARIA raportuje postęp naukowy |
| 25–49 | Event `first_signal_limes` możliwy |
| 50–74 | Event `dms_confirmed` możliwy; Yuki na skraju czegoś |
| 75–99 | Analiza biologiczna możliwa; zakończenie TRIUMF dostępne |
| 100 | Zakończenie TRIUMF lub PYRRUSOWE odblokowane |

**Modyfikatory:**

| Zdarzenie | LifeData |
|---|---|
| M03 Obserwacja kosmiczna (sukces) | +1–2 |
| M07 Spektroskopia dalekiego zasięgu (sukces) | +4 |
| M10 Skanowanie atmosferyczne (sukces) | +3 |
| M11 Mapowanie powierzchni (sukces) | +2 |
| M12 Ekspedycja atmosferyczna (sukces pełny) | +8 |
| M14 Analiza biologiczna (sukces pełny) | +10 |
| Event `false_biosignature` | −15 |
| Sensory <40% przez 3+ tury | −1/turę |
| Lab <25% | blokada wzrostu |

---

## 7. TABELA PODSUMOWUJĄCA MISJE MVP

| ID | Nazwa | Typ | Kto | Tury | Akt | Ryzyko |
|---|---|---|---|---|---|---|
| M01 | Przegląd systemu | journey | varies | 1 | I–V | niskie |
| M02 | Naprawa awaryjna | journey | Grzech | 1 | I–V | średnie |
| M03 | Obserwacja kosmiczna | journey | Yuki/Jakub | 1 | I–V | niskie |
| M04 | Sesja medyczna | journey | Amara | 1 | I–V | niskie |
| M05 | Kalibracja | journey | Felix/Lena | 1 | I–V | brak |
| M06 | Transmisja do Ziemi | journey | Jakub | 1 | I–V | brak |
| M07 | Spektroskopia dalekiego zasięgu | approach | Yuki+Felix | 1 | IV | niskie |
| M08 | Protokół orbitalny | approach | Lena+Jakub | 1 | IV | niskie |
| M09 | Przygotowanie laboratorium | approach | Amara+Yuki | 1 | IV | niskie |
| M10 | Skanowanie atmosferyczne | orbital | Yuki | 1 | IV | niskie |
| M11 | Mapowanie powierzchni | orbital | Felix | 1 | IV | niskie |
| M12 | Ekspedycja atmosferyczna | surface | Yuki+Lena | **2** | IV | **wysokie** |
| M13 | Protokół COSPAR | surface | Amara+Yuki | **2** | IV | średnie |
| M14 | Analiza biologiczna | surface | Yuki+Felix | 1 | IV–V | **krytyczne** |

---

## 8. NARRACYJNA MAPA ODKRYCIA

```
Akt II–III                    Akt IV                      Akt V
│                             │                           │
▼                             ▼                           ▼
M03 Obserwacja          M07 Spektroskopia          M14 Analiza
(LifeData gromadzone    dalekiego zasięgu          biologiczna
 przez dziesiątki       (pierwsze odczyty)         (definitywna)
 tur rejsu)                    │                          │
                               ▼                          ▼
                        EVENT: first_signal_limes   EVENT: dms_confirmed
                               │                    (lub: false_biosignature)
                               ▼
                        M10 Skanowanie              ZAKOŃCZENIE
                        atmosferyczne               ├── TRIUMF
                               │                    ├── PYRRUSOWE
                               ▼                    └── CICHY POWRÓT
                        M12 Ekspedycja
                        (high stakes)
                               │
                               ▼
                        M13 COSPAR (obowiązkowe)
                               │
                               ▼
                        M14 Analiza
```

---

## Missions update — v1.0

**Ukończono:**
- 14 misji MVP z pełnymi opisami, checkami i efektami
- 3 kategorie: podróżne, podejście Limes, powierzchniowe
- Mechanika misji wieloturowych (blokowanie, przerywanie, kolizja z eventem)
- Wskaźnik LifeData z progami narracyjnymi
- Mapa narracyjna odkrycia od Aktu II do V
- Tabela podsumowująca wszystkie misje

**Otwarte pytania:**
- Czy M12 (ekspedycja) powinna mieć wariant bez lądowania?
  (orbitalny dropsondy — bezpieczniejsze, mniej efektywne)
- Czy Felix może prowadzić M14 solo jeśli Yuki jest niedostępna?
  (gorszy wynik, ale mission continues)
