# 05 — Ship Systems
## Systemy Statku *Kairos* | Wersja 1.0

> Ten plik pokrywa systemy operacyjne statku: kadłub, sensory, laboratorium,
> komunikację, medbay, kapsułki torporu i warsztat inżyniera.
> Systemy ECLSS (TLEN, WODA, ŻYWNOŚĆ, CO₂, Sabatier, WRS) są w `mechanika/03-resources.md`.
> Reaktor fuzyjny — zasilanie pokryte w `mechanika/03-resources.md`, tu tylko powiązania.
> Ostatnia aktualizacja: 2026-05

---

## ZASADA NACZELNA

Systemy statku to kontekst w którym żyją parametry załogi i zasoby.
Nie są osobnym bytem — są warstwą między kosmosem a ludźmi wewnątrz.

Każdy system ma:
- **pasywną degradację** *(czas niszczy wszystko)*
- **awarię** *(zdarzenie które niszczy szybciej)*
- **efekt niskiego poziomu** *(co czujesz zanim system padnie)*
- **efekt zera** *(co się dzieje kiedy pada)*
- **koszt naprawy** *(ile CZĘŚCI, jaka trudność, kto naprawia)*

*Kairos* dotrze do celu stary. Grzech będzie naprawiał naprawy napraw.
To nie jest mechanika tła — to jest czas na statku.

---

## PODZIAŁ SYSTEMÓW

```
SYSTEMY STATKU *KAIROS*
│
├── Z mechanika/03-resources.md (ECLSS):
│   ├── CO₂ Skruber
│   ├── Reaktor Sabatiera
│   ├── Water Recovery System
│   ├── Hydroponika
│   ├── Bioreaktory
│   └── Reaktor Fuzyjny (zasilanie)
│
└── Ten plik (systemy operacyjne):
    ├── Kadłub (Hull)
    ├── Sensory (Sensors)
    ├── Laboratorium (Lab)
    ├── Komunikacja (Comm)
    ├── Baza Medyczna (Medbay)
    ├── Kapsułki Torporu (Torpor Chambers) × 7
    └── Warsztat Inżyniera (Workshop)
```

---

## 1. KADŁUB — HULL

### Funkcja
Ochrona przed próżnią, promieniowaniem i mikrometeorytami.
Przy prędkości 0,07c — ziarno kurzu ma energię kinetyczną bomby.

### Dane źródłowe
Przy prędkości 0,07c cząstka o masie 0,1 g uderza z energią ~220 GJ.
Osłona Whipple'a (wielowarstwowy bufor) absorbuje cząstki <1 mm.
Obiekty >1 cm: konieczny unik lub uszkodzenie strukturalne.
Korozja przez promieniowanie GCR: materiały aluminidkowe tracą
~0,15% wytrzymałości rocznie przy pełnej ekspozycji.

### Skala i efekty

| Sprawność | Stan | Efekt mechaniczny |
|---|---|---|
| 85–100% | **Integralny** | Brak modyfikatorów |
| 65–84% | **Uszkodzony** | Radiation dla aktywnej załogi: +0,3 mSv/dzień ponad baseline |
| 40–64% | **Naruszony** | Radiation: +0,8 mSv/dzień; Morale całej załogi: −5 natychmiast |
| 20–39% | **Krytyczny** | Radiation: +2,0 mSv/dzień; Morale: −15; ryzyko nagłej dekompresji (event) |
| 5–19% | **Katastrofalny** | Dekompresja możliwa w każdej turze bez naprawy |
| 0% | **KONIEC GRY** | Dekompresja — cała aktywna załoga |

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Mikrouderzenia podczas rejsu | −0,2%/turę (nieustanna erozja przy 0,07c) |
| Solar flare (zdarzenie) | −5 do −20 jednorazowo |
| Kolizja z obiektem >1 cm (zdarzenie) | −10 do −35 jednorazowo |
| Korozja radiacyjna (akumulacja) | −0,1%/turę przy sprawności <70% |

**Utrzymanie przez Grzecha** (INŻYNIERIA difficulty 6, brak CZĘŚCI):
Zatrzymuje pasywną degradację na tę turę. Nie naprawia aktywnych uszkodzeń.

### Naprawa

| Zakres naprawy | Koszt CZĘŚCI | Trudność | Postać |
|---|---|---|---|
| Mała łatka (przywraca ≤10%) | 4 | 6 | Grzech lub Lena |
| Naprawa modułu (przywraca 10–30%) | 10 | 9 | Grzech |
| Naprawa krytyczna (przywraca >30%) | 20 | 12 | Grzech (tylko) |

### Narracyjny kontekst
Kadłub jest niewidoczny kiedy działa.
Widoczny gdy nie działa — jako echo w metalowej ścianie,
jako temperatura powietrza która jest o pół stopnia za niska,
jako dźwięk którego Grzech słucha w nocy i mówi tylko „mhm".

> *„Kadłub to nie jest granica między nami a kosmosem.
> Kadłub to my mówimy kosmosowi: jeszcze nie."*
> — Grzech, dzień 847 misji.

---

## 2. SENSORY — SENSORS

### Funkcja
Trzy warstwy detekcji:
1. **Nawigacyjne** — śledzenie gwiazd, kurs, korekty trajektorii
2. **Hazardowe** — wczesne ostrzeżenie przed obiektami, rozbłyskami
3. **Naukowe** — spektroskopia atmosferyczna, biosygnatury, dane z Limes

Bez sensorów naukowych Yuki nie ma czym szukać życia.
Bez nawigacyjnych Lena nie wie gdzie leci.
Bez hazardowych — nie wiadomo co nadchodzi.

### Dane źródłowe
Teleskopy spektroskopowe klasy JWST-successor: rozdzielczość spektralna
pozwala na detekcję O₂/CH₄ z odległości <3 lat świetlnych.
Kalibracja sensorów kosmicznych wymaga regularnej korekty
ze względu na termiczne odkształcenia struktury teleskopu.
Dryf kalibracyjny: ~0,5% na miesiąc bez korekty.

### Skala i efekty

| Sprawność | Stan | Efekt mechaniczny |
|---|---|---|
| 85–100% | **Kalibrowany** | NAUKA Yuki: +1 do checków biosygnatur; pełne wczesne ostrzeżenie |
| 65–84% | **Dryf kalibracyjny** | NAUKA Yuki: brak modyfikatora; wczesne ostrzeżenie: −30% zasięgu |
| 40–64% | **Degradacja** | NAUKA Yuki: −1; nawigacja: PILOTAŻ Leny +1 difficulty; LifeData: −30% akumulacji |
| 20–39% | **Ślepota daleka** | Brak biosygnatur; LifeData: 0; nawigacja: tylko lokalna |
| 5–19% | **Ślepota prawie pełna** | PILOTAŻ Leny: +2 difficulty; kursy wymagają recalkulacji co turę |
| 0% | **Ślepi** | Lot bez instrumentów; nawigacja tylko manualna; event `dms_confirmed` niemożliwy |

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Dryf kalibracyjny (termiczny) | −0,5%/turę bez korekty |
| Promieniowanie GCR (elektronika) | −0,3%/turę pasywnie |
| Mikrouderzenia w panel sensorowy | −0,2%/turę przy niskim Hull |
| Solar flare (przepięcie) | −8 do −25 jednorazowo |

**Kalibracja przez Felika lub Lena** (NAUKA lub PILOTAŻ difficulty 6, brak CZĘŚCI):
Zatrzymuje dryf kalibracyjny na turę. Felix może to robić jako część rutyny ARII.
Lena kalibruje sensory nawigacyjne niezależnie — jej trait i charakter.

### Naprawa

| Zakres naprawy | Koszt CZĘŚCI | Trudność | Postać |
|---|---|---|---|
| Rekalibracja (przywraca ≤15%) | 0 (tylko czas) | 6 | Felix / Lena / Yuki |
| Wymiana modułu (przywraca 15–40%) | 7 | 9 | Grzech + Felix |
| Naprawa główna (przywraca >40%) | 14 | 12 | Grzech (tylko) |

### Narracyjny kontekst
Sensory to oczy misji.
Yuki sprawdza odczyty każdego ranka. Nie dlatego że musi.
Dlatego że to jedyna rzecz która mówi jej że Limes naprawdę tam jest.

> *„Sprawdziłam sześć razy."*
> — Dr Yuki Tanaka, event `first_signal_limes`.

**Powiązanie z postacią:** Gdy sensory <65%, Yuki Morale spada o −3 każdą turę.
Nie dramatycznie. Cicho. Jak ktoś kto traci wzrok powoli.

---

## 3. LABORATORIUM — LAB

### Funkcja
Analiza naukowa: spektrometria mas, sekwencjonowanie genetyczne,
mikroskopia elektronowa, synteza i hodowla próbek biologicznych.
Protokoły kwarantanny COSPAR wymagają sprawnego Lab.

**Yuki bez działającego Lab jest jak chirurg bez sali operacyjnej.**

### Dane źródłowe
Wymagania protokołu COSPAR Category IV (planety potencjalnie habitowalne):
- Biohazard containment Level 3+
- Zdolność do analizy organicznej i nieorganicznej
- Systemy filtracji >99,99% (HEPA + UV + chemiczna)
- Redundancja wszystkich krytycznych funkcji

### Skala i efekty

| Sprawność | Stan | Efekt mechaniczny |
|---|---|---|
| 85–100% | **Pełna zdolność** | NAUKA Yuki: +1 do analizy; COSPAR pełne protokoły |
| 65–84% | **Ograniczenia** | NAUKA Yuki: brak modyfikatora; LifeData: −20% jakości |
| 40–64% | **Poważna degradacja** | NAUKA Yuki: −1; COSPAR protokoły: uproszczone (risk flag) |
| 20–39% | **Analiza prymitywna** | NAUKA Yuki: −2; brak możliwości analizy biologicznej |
| 5–19% | **Niezdatne** | Żadna analiza naukowa niemożliwa; event `dms_confirmed` niemożliwy |
| 0% | **Zniszczone** | Misja naukowa zakończona bez odkrycia |

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Zużycie odczynników i mediów | −0,3%/turę (nieodwracalne — brak uzupełnienia) |
| Wibracje statku (precyzja kalibracji) | −0,2%/turę |
| Awaria systemu chłodzenia próbek (zdarzenie) | −10 do −20 jednorazowo |

**Uwaga krytyczna:** Lab ma komponent CONSUMABLES (odczynniki, media) który
jest nieodwracalny — CZĘŚCI mogą naprawić sprzęt, ale nie uzupełnić odczynników.
Po 85+ turach aktywności bez specjalnych eventów dostarczających zapasy:
Lab max sprawność spada do 80% permanentnie.

**Utrzymanie przez Yuki** (NAUKA difficulty 6, brak CZĘŚCI):
Zoptymalizowane wykorzystanie odczynników — spowalnia degradację o 60% na tę turę.

### Naprawa

| Zakres naprawy | Koszt CZĘŚCI | Trudność | Postać |
|---|---|---|---|
| Naprawa sprzętu (przywraca do 40%) | 9 | 9 | Grzech + Yuki |
| Wymiana modułu analitycznego (>40%) | 16 | 12 | Grzech (tylko) |
| Odczynniki nie są naprawialne | — | — | — |

### Narracyjny kontekst
Laboratorium to jedyne miejsce na statku które jest wyłącznie Yuki.
Grzech naprawia sprzęt ale nie dotyka protokołów.
Jakub może wejść — ale zwykle puka.

Hodowane tu nasiona *Arabidopsis thaliana* — formalnie badanie botaniczne.
Nieformalnie: jedyna żywa rzecz poza ludźmi na tym statku przez 58 lat.
Jeśli Lab spada poniżej 40%, rośliny giną. To zdarzenie narracyjne, nie mechaniczne.
Yuki wie o tym zanim to nastąpi.

---

## 4. KOMUNIKACJA — COMM

### Funkcja
Łącze z Ziemią: transmisja danych naukowych, raporty misji,
wiadomości osobiste, rozkazy WABK.
Systemy wewnętrzne: komunikacja między modułami statku.
Beacon awaryjny: sygnał pozycji przy katastrofie.

### Dane źródłowe
Laser optyczny Deep Space Optical Communications (DSOC):
- 267 Mb/s przy odległości 0,2 AU
- Przy 1 ly: ~0,4 kb/s (degradacja z kwadratem odległości)
- Przy 14 ly: ~0,002 kb/s — każdy bajt to decyzja

**Zasada niezmienna:** Opóźnienie sygnału rośnie z odległością.
Sprawność systemu Comm wpływa na pasmo (bandwidth), nie na opóźnienie.
Opóźnienia nie da się naprawić. Dystans jest dystansem.

### Przepływ bandwidthu

```
Bandwidth = Sprawność_Comm × (1 / lata_świetlne²) × 267 Mb/s_baseline

Przykłady:
- Rok 1 (0,07 ly), Comm 100%: ~3,5 MB/dzień
- Rok 10 (0,7 ly), Comm 100%: ~36 KB/dzień
- Rok 30 (2,1 ly), Comm 100%: ~4 KB/dzień
- Rok 58 (4,06 ly), Comm 100%: ~1 KB/dzień
- Rok 58 (4,06 ly), Comm 50%: ~0,5 KB/dzień
```

*Dla gry: bandwidth jest zasobem który decyduje ile danych możesz wysłać do Ziemi per turę.
Implementacja szczegółowa: `mechanika/06-missions.md` (Akt IV).*

### Skala i efekty

| Sprawność | Stan | Efekt mechaniczny |
|---|---|---|
| 85–100% | **Pełne łącze** | Pełne bandwidth; wiadomości osobiste możliwe |
| 65–84% | **Zakłócenia** | Bandwidth: −25%; eventy wiadomości z Ziemi: −30% szans |
| 40–64% | **Degradacja** | Bandwidth: −60%; tylko raporty misji |
| 20–39% | **Krytyczne** | Bandwidth: −85%; tylko tekst, bez danych naukowych |
| 5–19% | **Awaryjne** | Tylko beacon pozycyjny + 10 znaków/turę |
| 0% | **Cisza** | Brak kontaktu z Ziemią; beacon awaryjny aktywny |

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Termiczne odkształcenie anteny (cykl słoneczny) | −0,4%/turę |
| Promieniowanie (elektronika lasera) | −0,3%/turę |
| Solar flare (przepięcie układów) | −6 do −18 jednorazowo |

**Utrzymanie przez Felixa** (KOMUNIKACJA difficulty 6, brak CZĘŚCI):
Felix kalibruje anteny i układy optyczne — spowalnia degradację o 70% na turę.
To jest jego codzienna rutyna. Robi to automatycznie jeśli jest aktywny.

### Naprawa

| Zakres naprawy | Koszt CZĘŚCI | Trudność | Postać |
|---|---|---|---|
| Naprawa elektroniki (przywraca ≤20%) | 3 | 6 | Felix |
| Wymiana modułu anteny (20–50%) | 6 | 9 | Grzech + Felix |
| Naprawa lasera optycznego (>50%) | 12 | 12 | Grzech (tylko) |

### Narracyjny kontekst
Comm to sznurek między statkiem a Ziemią.
W Akcie I sznurek jest gruby i żywy.
W Akcie III jest nitką.
W Akcie IV — piszesz do kogoś kto może nie żyć kiedy list dotrze.

**Powiązanie z postacią:** PAMIĘĆ Jakuba rośnie gdy Comm spada.
Nie dlatego że traci kontakt — dlatego że słyszy głosy coraz rzadziej
i zaczyna pamiętać je wyraźniej.

Event `late_letter` i `orders_for_someone_else` wymagają Comm >20%.
Jeśli Comm = 0 zanim nastąpią: gracze nie otrzymają tych eventów.
To jest zakończenie przez milczenie — nie narracyjny wybór, ale konsekwencja.

---

## 5. BAZA MEDYCZNA — MEDBAY

### Funkcja
Sala operacyjna, gabinet psychologiczny, apteka, izolatka kwarantanny.
Jedna osoba, dwie specjalizacje (Amara) — dwa razy więcej powodów
żeby sprzęt działał.

### Dane źródłowe
Chirurgia w warunkach mikrograwitacji wymaga specjalistycznego sprzętu:
- Systemy podciśnieniowe zamiast standardowego ssania krwi
- Stabilizatory pola operacyjnego (drgania statku)
- Autotransfuzer dla małego zespołu
- Psychiatria: terapia CBT, farmakoterapia (leki zużywają się nieodwracalnie)

**Leki** — jak odczynniki w Lab — mają komponent CONSUMABLES.
Psychotropy, antybiotyki, środki przeciwbólowe: skończony zapas, bez uzupełnienia.

### Skala i efekty

| Sprawność | Stan | Efekt Medyczny / Psychologiczny |
|---|---|---|
| 85–100% | **Pełna zdolność** | MEDYCYNA Amary: +1; max Health recovery: +15 |
| 65–84% | **Ograniczenia sprzętu** | MEDYCYNA Amary: brak mod; max Health recovery: +10 |
| 40–64% | **Poważna degradacja** | MEDYCYNA Amary: −1; max Health recovery: +6; psychotropy ograniczone |
| 20–39% | **Prymitywne** | MEDYCYNA Amary: −2; max Health recovery: +3; tylko zabiegi ratujące życie |
| 5–19% | **Polowe** | MEDYCYNA Amary: −3; max Health recovery: +1; brak operacji |
| 0% | **Brak bazy** | Amara działa bez sprzętu — max Health recovery: 0; Morale Amary: −20 permanentne |

**Komponent consumables:**
Po 60+ turach aktywności: leki psychiatryczne wyczerpują się.
MEDYCYNA Amary dla Morale recovery: −2 permanentnie.
*(Amara potrafi leczyć przez rozmowę. Ale niektóre rzeczy wymagają farmacji.)*

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Zużycie leków i materiałów jednorazowych | −0,2%/turę (nieodwracalne) |
| Degradacja sprzętu elektronicznego | −0,2%/turę |
| Awaria sterylizatora (zdarzenie) | −8 do −15 jednorazowo |

**Utrzymanie przez Amarę** (MEDYCYNA difficulty 6, brak CZĘŚCI):
Amara optymalizuje zużycie materiałów — spowalnia degradację o 50%.
Ale każda tura w której Amara utrzymuje Medbay, nie może skupić się na czymś innym.
To jest wybór który gracz musi zaakceptować: Amara jako serwis techniczny
albo Amara jako psycholog aktywny.

### Naprawa

| Zakres naprawy | Koszt CZĘŚCI | Trudność | Postać |
|---|---|---|---|
| Naprawa elektroniki medycznej (≤15%) | 4 | 6 | Grzech |
| Wymiana modułu (15–40%) | 8 | 9 | Grzech + Amara |
| Remont pełny (>40%) | 14 | 12 | Grzech (tylko) |
| Leki — nie naprawialne | — | — | — |

### Narracyjny kontekst
Medbay jest jedynym miejscem gdzie można płakać.
Amara to wie. Projektowała sesje tak, żeby ludzie nie musieli przechodzić
przez wspólną część statku żeby tam dotrzeć.

> *„Zna stan każdej osoby na statku lepiej niż ta osoba zna sama siebie.
> Ma prywatne logi których nie wysyła na Ziemię.
> Nie dlatego że kłamie. Dlatego że Ziemia by nie zrozumiała."*
> — `docs/FABULA.md`, profil Amary.

Jeśli Medbay spada poniżej 40% i jednocześnie Amara ma Morale <50:
event specjalny — Amara przychodzi do kapitana i mówi coś czego nie powiedziała nigdy wcześniej.
*(Tylko raz. Tylko przy tym warunku.)*

---

## 6. KAPSUŁKI TORPORU — TORPOR CHAMBERS

### Funkcja
Siedem kapsuł hibernacji (po jednej per członek załogi).
System ogrzewania, chłodzenia, monitorowania biometrii, farmacji torporu.
Bez działających kapsuł rotacja torporu jest niemożliwa.

### Dane źródłowe
SpaceWorks NASA NIAC (Bradford, 2013/2018) — torpor medyczny:
Temperatura ciała w torpor: 32–34°C (hipotermia kontrolowana).
Automatyczne systemy monitorowania: ciśnienie, saturacja, EEG, hormony.
Zużycie O₂ w torpor: −95% vs stan aktywny.
Ryzyko powikłań przy przedwczesnym wybudzeniu: hipotermia łagodna, dezorientacja, stres kardiologiczny.

### Siedem kapsuł — każda niezależna

Każda kapsuła ma własną sprawność (0–100%).
Kapsuły degradują niezależnie — jedna może być sprawna gdy inne nie.

| Sprawność kapsuły | Stan | Efekt |
|---|---|---|
| 85–100% | **Sprawna** | Torpor normalny; pełna redukcja radiacji i Fatigue |
| 65–84% | **Drobny problem** | Event `torpor_anomaly` możliwy dla tej osoby (waga +2) |
| 40–64% | **Ryzyko** | Event `torpor_anomaly` dla tej osoby: waga +5; Health postaci po torpor: −5 extra |
| 20–39% | **Niebezpieczna** | Kapsuła nie zalecana; wymuszony torpor: Health −15 natychmiast |
| 5–19% | **Awaryjna** | Torpor w tej kapsule może zabić — check MEDYCYNA difficulty 12 przed użyciem |
| 0% | **Niezdatna** | Postać nie może wchodzić w torpor; jest permanentnie aktywna |

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Mechaniczne zużycie systemów ogrzewania/chłodzenia | −0,3%/turę per kapsuła |
| Farmakologia torporu (wyczerpanie zapasów) | −0,1%/turę (komponent consumables) |
| Mikrowyładowania elektryczne (elektronika biomonitoringu) | −0,2%/turę |

**Utrzymanie przez Grzecha i Amarę** *(wspólne):*
- Grzech: mechanika kapsuł (INŻYNIERIA difficulty 6, brak CZĘŚCI)
- Amara: farmakologia i biometria (MEDYCYNA difficulty 6, brak CZĘŚCI)
- Jeśli oboje aktywni i utrzymują: −80% degradacji per turę dla wszystkich kapsuł
- Jeśli tylko Grzech: −50% dla mechaniki, farmakologia degraduje normalnie
- Jeśli tylko Amara: −50% dla farmakologii, mechanika degraduje normalnie

**Wyjątkowa interakcja:** Event `mira_capsule_fault` odnosi się do tej mechaniki.
Kapsuła Miry po tym evencie może mieć sprawność 60% jeśli nie naprawiona.

### Naprawa

| Zakres naprawy | Koszt CZĘŚCI | Trudność | Postać |
|---|---|---|---|
| Naprawa mechaniczna kapsuły (≤20%) | 4 | 6 | Grzech |
| Wymiana modułu biomonitoringu (20–50%) | 8 | 9 | Grzech + Amara |
| Remont kapsuły (>50%) | 12 | 12 | Grzech (tylko) |
| Farmakologia — nie naprawialna | — | — | — |

### Narracyjny kontekst
Torpor to jedyna forma ciągłości na tym statku.
Bez kapsuł nie ma rotacji. Bez rotacji wszyscy są cały czas aktywni.
Przy 2 mSv/dzień per osoba aktywna — bez torporu misja skończy się szybciej
niż statek dotrze do celu.

Kapsuła to śmierć kontrolowana. Każde wybudzenie to mała zmartwychwstanie.
Grzech mówi że najlepszy sygnał że kapsuła jest sprawna
to gdy osoba w niej leży spokojnie i nic nie czuje.

---

## 7. WARSZTAT INŻYNIERA — WORKSHOP

### Funkcja
Centrum naprawcze statku. Drukarki 3D (metal, polymer, kompozyt).
Przechowywanie i organizacja CZĘŚCI. Diagnostyka systemów.
Grzechowe królestwo.

### Dane źródłowe
Drukarki 3D na statku klasy Kairos:
- Metal SLS (Selective Laser Sintering): części strukturalne, złącza
- FDM polymer: uszczelki, izolacje, osłony
- Composites: materiały specjalistyczne

Ograniczenie: bez oryginalnych schematów CAD z Ziemi,
wydruk złożonych modułów elektronicznych jest niemożliwy.
Warsztat naprawia — nie fabrykuje od zera.

### Skala i efekty

| Sprawność | Stan | Efekt mechaniczny |
|---|---|---|
| 85–100% | **Pełna zdolność** | Naprawy w normalnym koszcie CZĘŚCI |
| 65–84% | **Ograniczenia** | Każda naprawa: +1 CZĘŚCI (mniej efektywne) |
| 40–64% | **Poważna degradacja** | Każda naprawa: +2 CZĘŚCI; czas naprawy: ×1,5 (Fatigue Grzecha +10 per naprawa) |
| 20–39% | **Prymitywny** | Każda naprawa: +4 CZĘŚCI; tylko naprawy difficulty ≤9 możliwe |
| 5–19% | **Prowizoryczny** | Każda naprawa: +6 CZĘŚCI; tylko naprawy difficulty ≤6 możliwe |
| 0% | **Zniszczony** | Grzech naprawia bez sprzętu: każdy check INŻYNIERIA +3 difficulty |

### Degradacja pasywna

| Źródło | Szybkość |
|---|---|
| Zużycie drukarek i narzędzi | −0,4%/turę |
| Zużycie filamentów i proszków (consumables) | −0,2%/turę (nieodwracalne) |
| Awaria drukarki głównej (zdarzenie) | −15 do −25 jednorazowo |

**Warsztat naprawia sam siebie:** Grzech może poświęcić turę na naprawę Warsztatu.
INŻYNIERIA difficulty 6, CZĘŚCI −3. Przywraca ≤20% sprawności.
*(To jest jedyny system który może się sam regenerować — bo Grzech jest tu.)*

### Naprawa warsztatu przez Grzecha

| Zakres naprawy | Koszt CZĘŚCI | Trudność |
|---|---|---|
| Naprawa drobna (≤15%) | 3 | 6 |
| Wymiana drukarki (15–35%) | 8 | 9 |
| Remont pełny (>35%) | 15 | 12 |

### Narracyjny kontekst
Grzech zbiera kamienie z każdego miejsca gdzie pracował.
Siedemnaście kamieni. Kairos będzie osiemnaście.

Warsztat to jego przestrzeń. Jedyna na tym statku gdzie jest całkowita cisza
i jednocześnie dzieje się coś konkretnego. Naprawiasz albo nie naprawiasz.
Metal nie kłamie. Jeśli spasowane — trzyma. Jeśli nie — puszcza.

> *„Ludzie mówią 'naprawię to jutro'. Metal nie zna jutra.
> Metal zna teraz."*
> — Grzech.

---

## 8. MACIERZ PRIORYTETÓW NAPRAW

Gdy CZĘŚCI są ograniczone — co naprawiać pierwsze?

```
PRIORYTET 1 — ŚMIERĆ W GODZINACH BEZ NAPRAWY:
├── CO₂ Skruber (03-resources.md)
└── Reaktor Fuzyjny (03-resources.md)

PRIORYTET 2 — ŚMIERĆ W DNIACH:
├── Kadłub <20% (dekompresja ryzyko)
└── Water Recovery <20% (kaskada do TLEN)

PRIORYTET 3 — MISJA W NIEBEZPIECZEŃSTWIE:
├── Kapsułki Torporu <40% (rotacja niemożliwa → limit radiacji)
├── Reaktor Sabatiera (03-resources.md) (TLEN spada szybko)
└── Sensory <40% (odkrycie niemożliwe)

PRIORYTET 4 — DEGRADACJA DŁUGOTERMINOWA:
├── Laboratorium (misja naukowa)
├── Warsztat (każda naprawa drożeje)
└── Medbay (opieka medyczna)

PRIORYTET 5 — JAKOŚĆ ŻYCIA I POŁĄCZENIE Z DOMEM:
└── Komunikacja (nie ratuje życia, ale ratuje sens)
```

> **Uwaga projektowa:** Gracz rzadko będzie miał CZĘŚCI na wszystko.
> Macierz priorytetów to sugestia, nie nakaz — każdy wybór ma uzasadnienie
> narracyjne. Ktoś kto wybiera Komunikację przed Sensorami
> mówi coś o tym czego mu potrzeba.

---

## 9. GRZECH JAKO SERCE SYSTEMU

Grzech jest jedyną osobą która może naprawiać wszystkie systemy.
Ale nie może robić wszystkiego naraz.

**Per tura Grzech może:**
- Utrzymać (kalibracja/przegląd) maksymalnie **3 systemy** bez kosztu CZĘŚCI
- Naprawić **1 system** aktywnie (check + CZĘŚCI)
- Jeśli robi więcej: Fatigue Grzecha +15 per dodatkowa czynność

**Przy Fatigue >80:** check INŻYNIERIA −1 (Grzech jest wyczerpany)
**Przy Fatigue 100:** Grzech musi odpocząć — nie naprawia tej tury

**Przy Morale Grzecha <30:**
Grzech automatycznie odmawia niebezpiecznych napraw (difficulty 12+).
Mówi o tym wprost, jednym zdaniem.
To jest sygnał narracyjny — gdy Grzech odmawia, coś jest bardzo nie tak.

**Jeśli Grzech zginie:**
- Wszystkie naprawy difficulty ≥ 9 wymagają check z karzącym modyfikatorem −3
- Warsztat: +2 do kosztu CZĘŚCI wszystkich napraw
- Kadłub, Reaktor Fuzyjny: tylko Tymczasowe naprawy możliwe (do 50%)
- Gra może być kontynuowana — ale jest inną grą niż była.

---

## 10. MAPA INTERAKCJI SYSTEMÓW

```
REAKTOR FUZYJNY (zasilanie)
        │
        ├──── KADŁUB ────────────► ochrona przed kosmosem
        │         │
        │         └──► Radiation ↑ gdy niski
        │
        ├──── SENSORY ───────────► NAUKA Yuki (+ biosygnatury)
        │         │
        │         └──► PILOTAŻ Leny (+ nawigacja)
        │
        ├──── LABORATORIUM ──────► NAUKA Yuki (+ analiza)
        │         │
        │         └──► COSPAR protokoły (+ odkrycie)
        │
        ├──── KOMUNIKACJA ───────► Ziemia (+ PAMIĘĆ)
        │         │
        │         └──► eventy z Ziemi (+ wiadomości osobiste)
        │
        ├──── MEDBAY ────────────► MEDYCYNA Amary
        │         │
        │         └──► Health i Morale recovery (+ całość)
        │
        ├──── KAPSUŁKI TORPORU ──► rotacja załogi (+ Radiation)
        │         │
        │         └──► misja możliwa przez 58 lat
        │
        └──── WARSZTAT ──────────► efektywność napraw (+ CZĘŚCI)
                  │
                  └──► GRZECH (centrum sieci)
```

---

## Ship Systems update — v1.0

**Ukończono:**
- Siedem systemów operacyjnych z pełnymi profilami (skala, degradacja, naprawa)
- Dwuwarstwowy model: consumables (nienaprawialne) + hardware (naprawialne)
- Macierz priorytetów napraw jako narzędzie decyzyjne gracza
- Narracyjne powiązania każdego systemu z postacią
- Profil Grzecha jako centralnego węzła systemu
- Mapa interakcji między systemami

**Otwarte pytania:**
- Czy Komunikacja przy 0% generuje specjalne zakończenie *Cisza* automatycznie?
  *(Sugestia: tak, jeśli wszystkie forced events z Ziemi jeszcze nie nastąpiły.)*
- Ile kapsuł torporu musi działać żeby rotacja była możliwa?
  *(Sugestia: minimum 4 z 7 — żeby zawsze mógł być aktywny kapitan + 1 osoba.)*
