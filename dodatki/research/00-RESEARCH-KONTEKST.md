# Kontekst naukowy — Gra SF 2099: Pierwsza Misja Międzygwiezdna

> Ten plik to baza wiedzy naukowej do projektu gry. Wszystkie fakty są zweryfikowane.
> Użyj go jako fundamentu przy projektowaniu mechanik — każda mechanika powinna mieć pokrycie w nauce, ale najważniejsza jest grywawlność!

---

## 1. NAPĘD — wybierz jedną z 3 opcji (każda implikuje inną grę)

| Napęd | Prędkość | Czas do 4 ly | Masa paliwa | Ryzyko | Rozmiar misji |
|---|---|---|---|---|---|
| **Fuzja termojądrowa** (Daedalus/Icarus) | 0,045–0,12 c | 35–90 lat | 50 000 t D/³He | średnie | 50–200 osób aktywnych |
| **Antymateria** (beam-core) | do 0,5 c | 8–10 lat | 1 g (!) | katastroficzne | 12–20 osób |
| **Żagiel laserowy** (Breakthrough Starshot) | 0,2 c | 20 lat | brak (sondy!) | umiarkowane | 0 — tylko sondy! |

**Wybór dla gry**: hybryda fuzja + torpora lub antymateria + mała załoga.

---

## 2. CEL PODRÓŻY — fikcyjny układ, parametry wzorowane na nauce

**Wzorzec planety docelowej** (synteza TRAPPIST-1e + Teegarden b):
- Masa: 0,7–1,2 M⊕ (masa Ziemi)
- Temperatura równowagi: 240–290 K
- Atmosfera: O₂ + CH₄ + H₂O (biosygnatury — pary chemiczne wykryte przez teleskopy)
- Odległość od gwiazdy: strefa habitabilna M-dwarfa (czerwonego karła)
- Gwiazda: M-dwarf, T_eff ~2500–3500 K, wiek >1 Gyr
- Odległość od Ziemi: 12–40 lat świetlnych

**Jak wykrywamy życie — hierarchia biosygnatur:**
1. O₂ + CH₄ jednocześnie (niemożliwe bez życia — wzajemnie się niszczą)
2. Para wodna + O₃ (ozon)
3. DMS (dimetylosiarczek) — produkowany przez fitoplankton
4. Red Edge — odbicie światła przez chlorofil
5. UWAGA: każda z tych sygnatur może być fałszywie pozytywna (precedens K2-18b 2025)

---

## 3. ZAŁOGA — dane liczbowe do mechanik

**Rozmiar załogi (3 paradygmaty):**
- **Aktywna** (fuzja, długa podróż): 50–200 osób, pełna hierarchia, pokolenia
- **Torpor** (SpaceWorks NASA NIAC): 96 z 100 hibernowanych, 4 dyżurnych rotacyjnie
- **Statek pokoleniowy** (Smith 2014): minimum 14 000–44 000 osób (!), "safe figure 40 000"

**Specjalizacje kluczowe dla gry:**
- Dowódca / Zastępca dowódcy
- Inżynier ECLSS (systemy podtrzymywania życia)
- Lekarz (chirurgia + psychiatria — jedna osoba!)
- Astrobiolog (kontakt z życiem)
- Pilot / Nawigator
- Psycholog / Mediator
- Botanik (hydroponika / żywność)
- Operator AI / Informatyk
- Inżynier napędu
- Geolog planetarny

**Psychologia — twarde dane:**
- **Third-Quarter Phenomenon** (Kanas 2021): w 50–75% misji dramatyczny spadek morale
- **Mars-500** (520 dni): 2 z 6 osób odpowiadało za 85% konfliktów
- **Asthenia**: chroniczne zmęczenie po >6 mies. izolacji
- **Earth Out of View Effect**: szok psychologiczny gdy Ziemia znika

**Ciało — twarde dane do mechanik zdrowia:**
- Utrata gęstości kości: 1,5%/miesiąc bez sztucznej grawitacji
- Promieniowanie: 1,81 ± 0,33 mSv/dzień (GCR, 16 g/cm² osłony)
- Limit NASA: 470–620 mSv całkowite (przekroczenie = trwałe uszkodzenie)
- Zanik mięśni łydki: 15% po 6 mies.
- SANS: obrzęk mózgu (17% astronautów długotrwałych)

---

## 4. SYSTEMY STATKU — mechaniki zarządzania zasobami

**ECLSS (systemy podtrzymywania życia) — 4 podsystemy:**
1. **Woda**: recyrkulacja 98% (NASA 2023, Brine Processor Assembly)
2. **Tlen**: elektroliza wody → O₂, odzysk 93% (reakcja Sabatiera)
3. **CO₂**: pochłaniacze litowe + Sabatier, awaria = śmierć w godzinach
4. **Temperatura**: pasywne i aktywne chłodzenie, radiatory

**Żywność — mix 3 systemów:**
- Hydroponika (50%): sałata, kapusta, soybeans (NASA Veggie)
- Bioreaktory (30%): drożdże, algi Spirulina, fermentacja
- Druk 3D + zapasy (20%): cell-cultured meat, liofilizaty

**Energia:**
- Reaktor fuzyjny (integracja z napędem): 1,2–9,2 TW
- Zapasowe: ogniwa paliwowe, akumulatory

**Naprawy:**
- Drukarki 3D (all-metal, polymer, bioprinting)
- Roboty autonomiczne (maintenance bots)
- Zapas surowców: 50% masy statku to spare parts

---

## 5. ZAGROŻENIA — tabela dla event system

| Zagrożenie | Prawdopodobieństwo | Skutek | Czas reakcji |
|---|---|---|---|
| Awaria ECLSS-CO₂ | wysokie (lata misji) | śmierć w godzinach | natychmiastowy |
| Promieniowanie GCR przekroczenie | pewne po 5+ latach | nowotwory, SANS | tygodnie-lata |
| Zderzenie z pyłem (0,1 c+) | niskie | uszkodzenie osłony | sekundy |
| Konflikt załogi | wysokie (3. kwartał) | rozpad misji | tygodnie |
| Awaria reaktora | bardzo niskie | katastrofa | minuty |
| Choroba psychiczna załoganta | wysokie (izolacja) | dezorganizacja | tygodnie |
| Patogen z planety (po lądowaniu) | nieznane | pandemia zamknięta | godziny |
| Błąd AI | losowe | krytyczne decyzje | sekundy |

---

## 6. KOMUNIKACJA — mechaniki opóźnienia

**Realistyczne opóźnienia:**
- Przy 4 ly: 4 lata czasu przesyłu sygnału w jedną stronę
- Laser optyczny DSOC: 267 Mb/s przy 0,2 AU → ~kilka bitów/sekundę przy 4 ly
- Splątanie kwantowe: NIE działa jako FTL — to mit (no-communication theorem, fizyka 1978+)

**Dla gry:**
- Ziemia odpowiada po 4–40 latach (zależy od odległości)
- Każda decyzja operacyjna = pełna autonomia AI + załogi
- Transmisja danych = cenny zasób (bandwidth per day)
- Ostatni sygnał z Ziemi staje się coraz starszą "historią"

---

## 7. KONTAKT Z ŻYCIEM — protokoły i dylematy

**Skala złożoności życia (0–6):**
- 0: chemia prebiotyczna (aminokwasy, bez życia)
- 1: prokarioty (bakterie-like)
- 2: maty mikrobialne / stromatolity
- 3: eukariota / wielokomórkowość
- 4: rośliny / autotrofy makroskopowe
- 5: zwierzęta / system nerwowy
- 6: inteligencja techniczna

**Protokoły (realne — COSPAR 2020, IAA SETI 2025):**
- Forward contamination: zakaz skażenia planety ziemskimi mikrobami
- Backward contamination: zakaz powrotu bez kwarantanny
- Lockdown po pierwszej próbce: 72h minimum
- Powiadomienie Ziemi: obowiązkowe, ale odpowiedź za 4 lata

**Dylematy etyczne do RPG:**
- Czy ujawnić odkrycie od razu (4 lata zanim Ziemia potwierdzi)?
- Czy wylądować ryzykując skażenie (możliwe zabicie unikalnego życia)?
- Czy inteligentne życie ma prawo NIE być obserwowanym?
- Co gdy patogen jest nieznany — czy zaryzykować powrót?
- Kto decyduje gdy AI i dowódca się nie zgadzają?

---

## 8. KLUCZOWE LICZBY do mechanik (copy-paste do kodu/danych)

```
PODRÓŻ:
  prędkość_rejsu = 0.045–0.12 c
  czas_do_celu = 35–90 lat (fuzja)
  opóźnienie_sygnału = 4–40 lat (light years)
  
PROMIENIOWANIE:
  dawka_dzienna = 1.81 mSv/dzień
  limit_NASA_kobiety = 470 mSv (całkowite)
  limit_NASA_mężczyźni = 620 mSv (całkowite)
  przekroczenie_limitu = trwały_debuff
  
ZASOBY:
  recyrkulacja_wody = 98%
  odzysk_O2 = 93%
  utrata_kości = 1.5%/miesiąc (bez grawitacji)
  
PSYCHOLOGIA:
  third_quarter_trigger = 50–75% czasu misji
  konflikt_eskalacja = po 6 mies. izolacji
  
HIBERNACJA (torpor):
  rotacja = 90 dni snu / 30 dni aktywności
  max_hibernowanych = 96/100
  ryzyko_neurodegeneracji = kumulatywne
  
ŻYWNOŚĆ:
  hydroponika = 50% diety
  bioreaktory = 30% diety
  zapasy_emergency = 20% + 2-letni bufor
  
POPULACJA_MIN (statek pokoleniowy):
  bezpieczny_próg = 40,000 osób
  absolutne_minimum = 14,000 osób
```

---

## 9. INSPIRACJE GATUNKOWE (co łączy mechaniki)

**Mechanika core:**
- Manager + RPG dice-check (jak Disco Elysium)
- Decyzje mają konsekwencje odroczonych w czasie (jak FTL)
- Zarządzanie zasobami z losowymi eventami (jak Rimworld / Oxygen Not Included)
- Fabularne wątki z moralnym ciężarem (jak This War of Mine)

**Co wyróżnia tę grę od innych SF:**
- Czas jest REALNY — lata misji = lata grania lub time-skip mechaniki
- Komunikacja z Ziemią staje się coraz bardziej abstrakcyjna
- Życie na statku TO Twoja rzeczywistość, nie Ziemia
- Nauka to nie fluff — każda mechanika ma fizyczne uzasadnienie

---

*Źródła: NASA, ESA, COSPAR, arXiv, Science 2019 (Twin Study), Kanas & Manzey, Long et al. JBIS, Smith Acta Astronautica 2014, Bradford SpaceWorks NIAC 2013/2018, IAA SETI Protocols 2025.*
