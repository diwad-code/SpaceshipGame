# 04 — Crew
## Mechanika Załogi | Wersja 1.0

> Plik oparty na profilach fabularnych z `docs/FABULA.md`.
> Każda liczba ma uzasadnienie naukowe lub narracyjne.
> Parametry bez uzasadnienia nie istnieją.
> Ostatnia aktualizacja: 2026-05

---

## ZASADA NACZELNA

Załoga to nie zasoby. Zasoby się zużywają i uzupełniają.
Ludzie się zmieniają. Każdy parametr mówi coś o człowieku,
nie o suwaku w interfejsie.

Mechanika ma to odzwierciedlać.

---

## 1. PARAMETRY POSTACI

Każdy członek załogi (włącznie z kapitanem) posiada cztery parametry bazowe
i jeden parametr akumulacyjny. Kapitan posiada dodatkowo system
sześciu głosów wewnętrznych — opisany osobno w sekcji 5.

---

### 1.1 ZDROWIE (Health) — skala 0–100

Reprezentuje kondycję fizyczną: sprawność, brak urazów, odporność
na warunki panujące na statku.

**Źródła degradacji (per cykl aktywności — ~30 dni):**
- Standardowa degradacja bez sztucznej grawitacji: **-1,5 pkt/miesiąc**
  *(utrata gęstości kości, NASA Twin Study — dane z `dodatki/research/`)*
- Uraz w zdarzeniu: **-5 do -20 pkt** (zależnie od eventu)
- Choroba: **-2 do -8 pkt/cykl** bez interwencji medycznej
- Promieniowanie >50% limitu: **-1 pkt/miesiąc** (kumulatywny debuff)

**Źródła regeneracji:**
- Opieka medyczna (Dr. Nwosu): **+5 do +15 pkt** (zależnie od checkupu)
- Odpoczynek w torpor: **-0,3 pkt/miesiąc** (degradacja mocno zwolniona, nie zatrzymana)
- Zdarzenie: niektóre eventy medyczne dają regenerację

| Zakres | Stan | Efekt mechaniczny |
|---|---|---|
| 85–100 | **Sprawny** | Brak modyfikatorów |
| 60–84 | **Zmęczony** | Skill checks: −1 do wszystkich |
| 35–59 | **Ranny** | Skill checks: −2; wymaga opieki medycznej |
| 10–34 | **Krytyczny** | Skill checks: −3; nie może samodzielnie pełnić funkcji |
| 1–9 | **Umierający** | Wymaga natychmiastowej interwencji lub śmierć |
| 0 | **Śmierć** | Nieodwracalne |

> **Uwaga projektowa:** śmierć postaci jest możliwa i narracyjnie istotna.
> Nie jest automatyczna — poprzedza ją stan Krytyczny który daje graczowi okno decyzji.
> Permanentna śmierć następuje gdy gracz nie podejmie działania lub check zakończy się
> porażką kaskadową przy stanie Umierający.

---

### 1.2 MORALE — skala 0–100

Reprezentuje stan psychiczny: wolę działania, zaufanie do misji i do innych,
odporność na izolację i presję.

**Źródła degradacji:**
- Standardowa izolacja: **-2 pkt/miesiąc** aktywności
- Torpor (psychologicznie niejednoznaczny): **-3 pkt/cykl** po wybudzeniu
  *(subiektywne poczucie utraty ciągłości czasu)*
- Konflikt interpersonalny: **-5 do -15 pkt** (zdarzenie)
- Third Quarter (50–75% misji): automatyczny trigger **-10 do -20 pkt** (patrz: sekcja 3)
- Śmierć członka załogi: **-15 pkt** dla całej aktywnej załogi
- Wiadomość z Ziemi — zła wiadomość: **-8 pkt**
- Fałszywa biosygnatura (dotyczy głównie Yuki): **-20 pkt**

**Źródła regeneracji:**
- Interwencja psychologiczna (Dr. Nwosu): **+5 do +12 pkt**
- Sukces misji: **+8 do +15 pkt**
- Pozytywna wiadomość z Ziemi: **+5 pkt**
- Zdarzenia narracyjne (muzyka Miry, żarty Grzecha, etc.): **+3 pkt** dla wskazanej postaci

| Zakres | Stan | Efekt mechaniczny |
|---|---|---|
| 80–100 | **Zdeterminowany** | Skill checks: +1; blue options dostępne |
| 55–79 | **Stabilny** | Brak modyfikatorów |
| 30–54 | **Zachwiany** | Skill checks: −1; ryzyko incydentów interpersonalnych |
| 10–29 | **Załamany** | Skill checks: −2; może odmówić przydziału zadania |
| 0–9 | **Granica** | Ryzyko mutiny lub psychologicznego krachu |

---

### 1.3 ZMĘCZENIE (Fatigue) — skala 0–100

Reprezentuje krótkoterminowe wyczerpanie fizyczne i psychiczne.
Nie jest stanem chronicznym — resetuje się po odpoczynku lub torpor.

**Źródła wzrostu:**
- Każde przydzielone zadanie: **+10 do +25 pkt** (zależnie od intensywności)
- Zdarzenie kryzysowe: **+15 do +30 pkt**
- Brak odpoczynku przez dwa cykle: **+10 pkt automatycznie**

**Źródła redukcji:**
- Odpoczynek (pełny cykl snu): **−30 pkt**
- Torpor: **reset do 0**

| Zakres | Stan | Efekt mechaniczny |
|---|---|---|
| 0–40 | **Wypoczęty** | Brak modyfikatorów |
| 41–70 | **Zmęczony** | Brak modyfikatorów (widoczne w dialogach) |
| 71–90 | **Wyczerpany** | Skill checks: −1 |
| 91–100 | **Limit** | Skill checks: −2; wymagany odpoczynek przed kolejnym zadaniem |

---

### 1.4 PROMIENIOWANIE (Radiation) — skala akumulacyjna [mSv]

Promieniowanie kosmiczne (GCR — Galactic Cosmic Radiation) akumuluje się
przez całą misję i nie resetuje się. Jest nieodwracalne.

**Dane źródłowe (NASA/MSL RAD, 2013):**
- Baseline GCR na głębokiej przestrzeni kosmicznej: **1,81 mSv/dzień**
- Przy standardowej osłonie 16 g/cm² aluminium aluminium
- Jeden cykl aktywny (~30 dni): **+54 mSv**
- Jeden cykl torporu (~90 dni): **+16 mSv** (redukcja o 90% dzięki pozycji i częściowej dodatkowej osłonie kapsuły torporu)

**Limity NASA (REID 3% — limit ryzyka nowotworu):**
- Kobiety: **470 mSv** całkowite
- Mężczyźni: **620 mSv** całkowite

**Progi i efekty:**

| Próg | Efekt |
|---|---|
| <25% limitu | Brak efektów mechanicznych |
| 25–50% limitu | Informacja narracyjna (wyniki badań Amary) |
| 50–75% limitu | Health: **−1 pkt/miesiąc** permanentny debuff |
| 75–90% limitu | Health: **−2 pkt/miesiąc**; ryzyko zdarzenia medycznego per cykl |
| >90% limitu | Health: **−3 pkt/miesiąc**; obligatoryjna konsultacja z Amarą |
| 100% limitu | Zdarzenie krytyczne — permanentne uszkodzenie zdrowia lub śmierć |

> **Uwaga:** Solar flare (zdarzenie losowe) może jednorazowo dodać **+50 do +120 mSv**
> jeśli załoga nie schroni się w centralnym module osłoniętym.

---

## 2. PROFILE STARTOWE ZAŁOGI

### Commander Jakub Nowak — Kapitan

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 100 | Start misji, pełna sprawność |
| Morale | 80 | Podekscytowany i pełen determinacji — ale Paweł ma 20 lat |
| Fatigue | 0 | Świeży start |
| Radiation | 0 | Dzień 1 |

**Skille kapitana** (skala 1–10):

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| NAUKA | 7 | 15 lat pracy naukowej. Tu jest w domu. |
| DOWODZENIE | 5 | Kompetentny, ale to nie jego żywioł — on planuje, nie rozkazuje. |
| PRZETRWANIE | 5 | Pragmatyczny gdy musi. Potrafi podjąć zimną decyzję. |
| KOMUNIKACJA | 5 | Dobry w perswazji akademickiej, słabszy w kryzysowej |
| PILOTAŻ | 2 | Wie teorię, nie ma praktyki |
| INŻYNIERIA | 3 | Rozumie systemy, nie naprawia |
| MEDYCYNA | 2 | Pierwsza pomoc. Nic więcej. |

**Głosy wewnętrzne** (startowe wartości — patrz sekcja 5):
DOWODZENIE 5 | EMPATIA 4 | NAUKA 7 | PRZETRWANIE 5 | PAMIĘĆ 6 | SYGNAŁ 3

**Trait startowy:** *Architekt misji*
> Kiedy misja jest pod bezpośrednią presją (zasoby <30% lub morale statku <40),
> NAUKA i PRZETRWANIE otrzymują **+1** do wszystkich checków.

---

### Mira Osei — Zastępczyni Dowódcy (XO)

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 100 | — |
| Morale | 75 | Startuje niżej niż inni. Wie że powinna dowodzić. |
| Fatigue | 0 | — |
| Radiation | 0 | — |

**Skille:**

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| DOWODZENIE | 8 | Naturalna dowódczyni. Lepsze wskaźniki niż Jakub. |
| PILOTAŻ | 7 | Pilot testowy ESA. Trzy misje dowodzone. |
| KOMUNIKACJA | 7 | Negocjuje, mediuje, słucha aktywnie. |
| PRZETRWANIE | 6 | Dowódca misji księżycowej — widziała kryzysy. |
| INŻYNIERIA | 4 | Podstawy operacyjne. Nie mechanik. |
| NAUKA | 3 | Wystarczające do czytania raportów. |
| MEDYCYNA | 2 | Pierwsza pomoc. |

**Trait startowy:** *Zimna głowa*
> W sytuacjach kryzysowych (morale całego statku <40 lub Health dowolnej postaci <35):
> DOWODZENIE Miry +**2**.
> *(Właśnie wtedy gdy inni panikują, Mira myśli najwyraźniej.)*

---

### Tomasz „Grzech" Grzegorzewski — Główny Inżynier

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 97 | Stare urazy z Meridian. Nigdy w pełni nie wygoiły. |
| Morale | 80 | Spokojny profesjonalista. Zaakceptował misję jak każdą inną. |
| Fatigue | 0 | — |
| Radiation | 0 | — |

**Skille:**

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| INŻYNIERIA | 9 | 20 lat pracy w terenie. Naprawiał rzeczy które nie powinny działać. |
| PRZETRWANIE | 8 | Wypadek na Meridian coś w nim ukształtował. |
| NAUKA | 4 | Praktyczna. Czyta manuały i dane systemów. |
| KOMUNIKACJA | 4 | Mówi wprost. Nie zawsze to pomaga. |
| MEDYCYNA | 3 | Polowa. Szwała rany, nastawiał złamania. |
| DOWODZENIE | 3 | Nie dowodzi — naprawia. |
| PILOTAŻ | 2 | Teoria. |

**Trait startowy:** *Śląski sposób*
> Nieudany check INŻYNIERIA nigdy nie kończy się pełną porażką.
> Grzech zawsze wyciągnie coś działającego — może brzydkiego, może
> tymczasowego, ale działającego.
> *(Porażka INŻYNIERIA = Częściowy sukces z komplikacją, nie Porażka.)*

---

### Dr Yuki Tanaka — Astrobiolog

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 95 | Lata pracy naukowej w złych warunkach. Spała za mało przez dekadę. |
| Morale | 85 | Ekscytacja misji. Ale K2-18b jest w podtekście. |
| Fatigue | 0 | — |
| Radiation | 0 | — |

**Skille:**

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| NAUKA | 9 | 47 prac naukowych. Najlepsza astrobiolog pokolenia. |
| KOMUNIKACJA | 6 | Potrafi tłumaczyć naukę — pisała dla mediów przez lata. |
| MEDYCYNA | 4 | Biologia podstawowa. Protokoły COSPAR. |
| PRZETRWANIE | 3 | Laboratorium to jej habitat. Nie kosmos. |
| INŻYNIERIA | 2 | Rozumie sprzęt naukowy. Nic więcej. |
| PILOTAŻ | 1 | Nie. |
| DOWODZENIE | 2 | Potrafi zarządzać projektem badawczym. Nie sytuacją kryzysową. |

**Trait startowy:** *Obsesja biosygnatur*
> NAUKA +**2** do wszystkich checków związanych z wykrywaniem i analizą życia.
> Gdy sygnatura okazuje się fałszywa: Morale **−20** (jednorazowo, per zdarzenie).
> *(K2-18b żyje w jej głowie. Każda fałszywa sygnatura to 2025 od nowa.)*

---

### Dr Amara Nwosu — Oficer Medyczny / Psycholog

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 100 | — |
| Morale | 82 | Profesjonalny dystans + genuina troska. Działa. |
| Fatigue | 0 | — |
| Radiation | 0 | — |

**Skille:**

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| MEDYCYNA | 9 | Chirurgia + psychiatria. Najlepiej wyszkolona z załogi. |
| KOMUNIKACJA | 8 | Słucha. Naprawdę słucha. |
| NAUKA | 5 | Biologia medyczna, farmakologia, neurologia. |
| PRZETRWANIE | 5 | Wie co zrobić gdy wszystko się wali. |
| DOWODZENIE | 4 | Autorytety medyczny — w sytuacji zdrowotnej jej słowo jest ostateczne. |
| INŻYNIERIA | 2 | Sprzęt medyczny. Nic więcej. |
| PILOTAŻ | 1 | Teoria. |

**Trait startowy:** *Widzę cię*
> Raz na akt Amara może ujawnić graczowi ukryty stan psychologiczny
> jednej wybranej postaci (prawdziwy stan Morale, ukryte napięcia relacyjne).
> *(Ma prywatne logi których nie wysyła na Ziemię.
> Wie o Mirze. Wie o Felixie. Wie o Jakubie.)*

---

### Lena Kowalska — Pilot / Nawigator

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 100 | — |
| Morale | 70 | Zostawiła kogoś na Ziemi. Startuje ciszej niż inni. |
| Fatigue | 0 | — |
| Radiation | 0 | — |

**Skille:**

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| PILOTAŻ | 10 | Najlepsza pilotka pokolenia. Wyniki symulacyjne: rekord WABK. |
| PRZETRWANIE | 7 | Trzy misje okołoziemskie, jedna księżycowa. Widziała awarie. |
| INŻYNIERIA | 5 | Musi rozumieć statek żeby go prowadzić. |
| NAUKA | 3 | Nawigacja celestialna. Fizykę rozumie operacyjnie. |
| KOMUNIKACJA | 3 | Lakoniczna. Mówi gdy musi. |
| DOWODZENIE | 2 | Lubi kiedy ktoś inny decyduje — ona wykonuje. |
| MEDYCYNA | 2 | Minimum. |

**Trait startowy:** *Czyste lądowanie*
> Krytyczne checki PILOTAŻ (trudność 12+) nigdy nie kończą się
> Porażką kaskadową — nawet na pełnej porażce coś zostaje kontrolowane.
> *(Lena traci zanim pozwoli żeby statek stracił za nią.)*

---

### Felix Ramos — Operator Systemów AI

| Parametr | Wartość startowa | Uzasadnienie |
|---|---|---|
| Health | 100 | — |
| Morale | 78 | Spokojny, filozoficzny. Ale coś w nim jest cicho. |
| Fatigue | 0 | — |
| Radiation | 0 | — |

**Skille:**

| Skill | Wartość | Uzasadnienie narracyjne |
|---|---|---|
| KOMUNIKACJA | 8 | Trzy lata rozmów z ARIĄ. Słyszy niuanse w każdym zdaniu. |
| NAUKA | 7 | Informatyka, lingwistyka obliczeniowa, systemy AI. |
| INŻYNIERIA | 6 | Systemy cyfrowe i infrastruktura AI statku. |
| MEDYCYNA | 3 | Podstawy. |
| PILOTAŻ | 3 | Teoretyczny. Zna nawigację z perspektywy systemów. |
| DOWODZENIE | 3 | Nie dowodzi. Analizuje. |
| PRZETRWANIE | 4 | Wystarczające. Raczej unika ryzyka niż go przeżywa. |

**Trait startowy:** *Język ARII*
> Gdy Felix jest aktywny (nie w torpor), ARIA wykonuje wszystkie
> zadania automatyczne z efektywnością +20% (bonus do checków gdzie
> ARIA asystuje technicznie).
> Gdy Felix jest w torpor przez >2 cykle z rzędu: ARIA wykazuje
> subtelne anomalie w logach. *(Gracz może to zauważyć lub nie.)*

---

## 3. TORPOR — MECHANIKA ROTACJI

System torporu oparty na SpaceWorks NASA NIAC (Bradford, 2013/2018).

**Standardowa rotacja:**
- 90 dni hibernacji → 30 dni aktywności → 90 dni hibernacji...
- Maksymalnie 6 osób w torpor jednocześnie
- Minimum 1 osoba aktywna przez cały czas (zwykle kapitan lub dyżurny)

**Efekty torporu na parametry:**

| Parametr | Efekt jednego cyklu torporu (90 dni) |
|---|---|
| Radiation | **+16 mSv** (95% redukcja vs aktywność) |
| Health | **−4,5 pkt** (degradacja kości/mięśni — 0,5% × 90 dni ÷ 10) |
| Morale | **−3 pkt** po wybudzeniu (dezorientacja temporalna) |
| Fatigue | **reset do 0** |

**Anomalie torporu** (eventy losowe, Akt II–III):
- Nieplanowane wybudzenie: postać budzi się poza harmonogramem
- Torpor failure: kapsuła wymaga naprawy (INŻYNIERIA check)
- Dezorientacja post-torpor: postać przez 1 cykl ma Fatigue +30 po wybudzeniu

---

## 4. SYSTEM SKILL CHECKÓW

### Formuła

```
Wynik = Skill (1–10) + Modyfikatory stanu + d6 (1–6)
Próg = Difficulty (3 / 6 / 9 / 12 / 15)
```

### Modyfikatory stanu

| Warunek | Modyfikator |
|---|---|
| Health 60–84 | −1 |
| Health 35–59 | −2 |
| Health <35 | −3 |
| Morale 30–54 | −1 |
| Morale 10–29 | −2 |
| Morale <10 | −3 |
| Fatigue 71–90 | −1 |
| Fatigue >90 | −2 |
| Radiation >50% limitu | −1 |
| Wyposażenie / sprzęt (zależnie od eventu) | +1 do +2 |
| Wsparcie kapitańskie (decyzja gracza) | +1 |
| Głos wewnętrzny kapitana (wysoki skill) | +1 |

### Progi trudności

| Difficulty | Opis | Przykład |
|---|---|---|
| 3 | Rutynowe | Codzienny odczyt statusu ECLSS |
| 6 | Wymagające | Naprawa drobnej usterki systemu |
| 9 | Trudne | Naprawa kaskadowej awarii ECLSS-CO₂ |
| 12 | Krytyczne | Operacja chirurgiczna w warunkach zerowej grawitacji |
| 15 | Graniczy z niemożliwym | Lądowanie z uszkodzonym systemem sterowania |

### Interpretacja wyników

| Wynik vs Próg | Rezultat | Opis |
|---|---|---|
| Próg +3 lub więcej | **Pełny sukces** | Dokładnie to co planowałeś |
| Próg +1 lub +2 | **Sukces z komplikacją** | Cel osiągnięty, ale coś kosztuje |
| Równy próg | **Częściowy sukces** | Połowa efektu lub z dużym kosztem |
| Próg −1 lub −2 | **Porażka** | Cel nieosiągnięty. Sytuacja nie pogorszona. |
| Próg −3 lub gorzej | **Porażka kaskadowa** | Porażka + coś innego się psuje |

### Blue check (niebieska opcja)

Dostępna gdy: **Skill postaci ≥ 8** ORAZ **Morale ≥ 60** ORAZ postać jest *specjalistą* w danej dziedzinie.

Efekt: nawet przy porażce brak Porażki kaskadowej. Minimum to Porażka.
*(Ekspert może nie dać rady — ale nie będzie katastrofy przez jego rękę.)*

---

## 5. GŁOSY WEWNĘTRZNE KAPITANA

Sześć skillów kapitana to nie tylko liczby — to perspektywy które
przemawiają do gracza podczas eventów. Wartości pokrywają się z skillem
do checków, ale ich narracyjna rola jest osobna.

### Progi aktywacji głosów

Głos pojawia się w oknie dialogowym zdarzenia gdy:
- Wartość ≥ 6: głos jest pewny, konkretny, mówi wprost
- Wartość 4–5: głos jest obecny ale niepewny, pyta zamiast stwierdzać
- Wartość ≤ 3: głos jest cichy lub milczy — pojawia się tylko w krytycznych momentach

| Głos | Skill | Start | Aktywacja |
|---|---|---|---|
| DOWODZENIE | Dowodzenie | 5 | Hierarchia, obowiązek, regulaminy WABK |
| EMPATIA | Komunikacja | 4 | Stan załogi, relacje, to co niepowiedziane |
| NAUKA | Nauka | 7 | Analiza, dane, cel misji, biosygnatury |
| PRZETRWANIE | Przetrwanie | 5 | Zasoby, ryzyko, zimna arytmetyka |
| PAMIĘĆ | — (pasywny) | 6 | Ziemia, Paweł, Agnieszka, to co zostawione |
| SYGNAŁ | — (pasywny) | 3 | Intuicja, anomalie, to czego dane nie tłumaczą |

> **PAMIĘĆ i SYGNAŁ** nie mają checków — są głosami czysto narracyjnymi.
> PAMIĘĆ rośnie automatycznie co Akt (wartość +1 per akt, max 10).
> SYGNAŁ rośnie po określonych zdarzeniach fabularnych — nie linearnie.

### Rozwój głosów

Skille kapitana rosną przez wybory narracyjne, nie przez grind.

Przykłady triggerów:
- DOWODZENIE +1: gracz podejmuje decyzję wbrew swojej preferencji dla dobra misji
- EMPATIA +1: gracz wybiera opcję związaną ze stanem psychicznym załogi gdy nie musi
- NAUKA +1: gracz zleca check naukowy zamiast przejść obok zdarzenia
- PRZETRWANIE +1: gracz podejmuje zimną kalkulacyjną decyzję która boli
- SYGNAŁ +1: gracz ufa przeczuciu które okazuje się słuszne

---

## 6. RELACJE MIĘDZY POSTACIAMI

Prosty trzypoziomowy system. Relacja jest asymetryczna —
A→B może być inne niż B→A.

| Poziom | Nazwa | Efekt mechaniczny |
|---|---|---|
| +1 | **Sojusz** | Postać B wykona ryzykowny check bez bonusu Morale gdy A o to poprosi |
| 0 | **Neutralna** | Standard |
| −1 | **Napięcie** | Postać B wymaga KOMUNIKACJA check od kapitana przed przydzieleniem zadania z B |
| −2 | **Konflikt** | Postać B odmawia współpracy z B. Wymaga interwencji Amary lub kapitana. |

### Relacje startowe

| Para | Relacja startowa | Uzasadnienie narracyjne |
|---|---|---|
| Jakub ↔ Mira | 0 / 0 *(komplikowana)* | Wiedzą o sobie wszystko. Nie powiedzą tego głośno. |
| Felix ↔ ARIA | specjalna *(poza skalą)* | Trzy lata trenowania. Język którego inni nie mają. |
| Grzech ↔ Lena | +1 / +1 | Wzajemny szacunek zawodowy. Mało mówią, dużo rozumieją. |
| Yuki ↔ Amara | +1 / 0 | Yuki ufa Amarze bardziej niż Amara ufa Yuki. |
| Jakub ↔ Grzech | 0 / +1 | Grzech szanuje tego który walczył o misję. Jakub go nie zna jeszcze. |

---

## 7. TORPOR A RELACJE

Kiedy dwoje ludzi śpi w tym samym cyklu — nic się nie zmienia.
Kiedy jedna osoba jest aktywna przez wiele cykli i wraca do
hibernacji, a inna jest aktywna po niej — między cyklami
jest narracyjna przepaść.

**Efekt mechaniczny torporu na relacje:**
- Relacja +1 bez kontaktu przez 2+ cykle torporu → może spaść do 0
- Relacja −1 bez kontaktu przez 2+ cykle → może spaść do −2
  *(resentyment rośnie kiedy nie ma rozmowy)*
- Relacja 0 przez 2+ cykle razem aktywnych → może wzrosnąć do +1
  *(bliskość wymaga czasu, nie tylko dobrych chęci)*

---

## 8. ŚMIERĆ POSTACI

Śmierć postaci jest możliwa. Nie jest automatyczna przy Health=0 —
gracze mają okno decyzji.

**Procedura:**
1. Health postaci spada do 1–9 (stan Umierający)
2. Amara otrzymuje automatyczne powiadomienie
3. Gracz ma 1 cykl aktywności żeby podjąć decyzję o interwencji
4. Jeśli MEDYCYNA check Amary ≥ 9: Health wraca do 20–30
5. Jeśli check porażka lub gracz nie interweniuje: Health → 0 (Śmierć)

**Konsekwencje narracyjne śmierci:**
- Morale całej aktywnej załogi: −15
- Kapitan otrzymuje specjalny tekst od każdego głosu wewnętrznego
- Zdarzenie narracyjne: ceremonia lub jej brak (wybór gracza)
- Jeśli śmierć to Yuki: trajektoria Aktu IV zmienia się dramatycznie
- Jeśli śmierć to Mira: Akt III kończy się inaczej
- Jeśli śmierć to Amara: nikt nie ma psychologa. Żadne Morale nie regeneruje się przez Akt IV.

---

## 9. KOMENTARZ PROJEKTOWY — CO NIE JEST TUTAJ

Poniższe mechaniki są **zarezerwowane** do czasu wypełnienia
pozostałych plików `mechanika/`:

- Formuły walki i combat damage → `mechanika/` nie gotowe
- Szczegółowe efekty traitów → `docs/IDEAS_LATER.md`
- System XP i progresji skillów → `docs/IDEAS_LATER.md`
- Frakcje i dyplomacja → `docs/IDEAS_LATER.md`

---

## Crew update — v1.0

**Ukończono:**
- Cztery parametry bazowe (Health, Morale, Fatigue, Radiation) z danymi NASA
- Profile startowe wszystkich 7 postaci ze skillami i traitami
- System skill checków z difficulty i interpretacją wyników
- Blue check (niebieska opcja) zgodna z FTL/DE inspiracją
- Głosy wewnętrzne kapitana z progami aktywacji
- System relacji interpersonalnych 3-poziomowy
- Mechanika torporu i jej efekty na parametry
