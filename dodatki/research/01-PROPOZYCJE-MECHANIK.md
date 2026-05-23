# PROMPT 01 — Propozycje mechanik gry SF 2099

> **Instrukcja użycia**: Wklej ten prompt + plik `00-RESEARCH-KONTEKST.md` do GPT-5.5 jako pierwszy komunikat w nowym czacie projektu. Zaczekaj na propozycje mechanik. NIE dawaj mu jeszcze dostępu do plików repo.

---

## TWOJA ROLA

Jesteś doświadczonym game designerem specjalizującym się w grach hybrydowych łączących manager/RPG. Znasz dobrze: FTL, Disco Elysium, Rimworld, This War of Mine, Oxygen Not Included, Dwarf Fortress.

Twoim zadaniem jest zaprojektowanie mechanik gry opartych ŚCIŚLE na dostarczonym researchu naukowym. Każda mechanika musi mieć uzasadnienie w nauce — nie wymyślamy "bo fajnie", ale "bo tak naprawdę działa fizyka/biologia/psychologia".

---

## OPIS GRY (co już wiemy)

**Gatunek**: hybryda managera statku kosmicznego + RPG fabularnego  
**Styl decyzji**: jak Disco Elysium — rzut kością + statystyki postaci decydują o wyniku  
**Setting**: rok 2099, pierwsza załogowa misja poszukiwania życia  
**Cel misji**: dolecieć do fikcyjnego układu planetarnego, znaleźć i sklasyfikować życie, wrócić (opcjonalnie)  
**Technologia**: napęd fuzji termojądrowej (linia Daedalus/Icarus), ~0,05–0,10 c  
**Czas podróży**: 40–80 lat (mechanika time-skip lub torpor)  
**Cel**: fikcyjna planeta wzorowana na TRAPPIST-1e / Teegarden b, 12–40 ly  
**Atmosfera**: twarda SF, realizm, moralny ciężar decyzji  

**Kontekst techniczny**: gra budowana w Phaser 3 + TypeScript + Vite. Mechaniki muszą być implementowalne w JavaScript/TypeScript, ale na tym etapie skupiamy się na design (nie na kodzie).

---

## TWOJE ZADANIE — KROK 1

Na podstawie dostarczonego pliku `00-RESEARCH-KONTEKST.md` zaproponuj mechaniki gry w następujących kategoriach. Dla każdej kategorii zaproponuj **2–3 warianty** o różnym stopniu złożoności (prosty / średni / zaawansowany), żebym mógł wybrać odpowiedni poziom.

### Kategoria A: NAPĘD I CZAS PODRÓŻY
Jak modelujemy wielodekadową podróż? Opcje do rozważenia:
- Time-skip z eventami losowymi
- Torpor/hibernacja jako mechanika
- Pokolenia na statku
- Kombinacja powyższych
*Pamiętaj: fizyczne dane o napędzie fuzyjnym, prędkość ~0,05 c, czas 40–80 lat*

### Kategoria B: ZARZĄDZANIE ZASOBAMI (ECLSS)
Jak modelujemy 4 podsystemy życiowe (woda 98%, tlen 93%, CO₂, żywność)?
- Czy każdy podsystem to osobny slider/wskaźnik?
- Jak modelujemy awarie kaskadowe?
- Jak wchodzi w to zarządzanie energią reaktora?
*Pamiętaj: dane liczbowe z researchu, np. recyrkulacja wody 98%, utrata O₂ 7%*

### Kategoria C: ZAŁOGA I RPG
Jak modelujemy 8–12 specjalistów z różnymi rolami?
- System statystyk postaci (co mierzyć?)
- Relacje między postaciami
- Degradacja psychiczna i fizyczna (kości -1,5%/miesiąc, promieniowanie kumulatywne)
- Third-Quarter Phenomenon jako mechanika
- Torpor i rotacja na dyżurach
*Pamiętaj: dane Mars-500, NASA Twin Study, limity dawek promieniowania*

### Kategoria D: DICE-CHECK (Disco Elysium style)
Jak modelujemy rzuty na wynik akcji?
- Jakie statystyki wpływają na rzut?
- Co wpływa na modyfikatory (promieniowanie, zmęczenie, relacje)?
- Jak modelujemy sukces częściowy vs pełny vs krytyczny
- Jak wyniki rzutów wpływają na długoterminowy stan gry

### Kategoria E: KOMUNIKACJA Z ZIEMIĄ
Jak modelujemy opóźnienie sygnału rosnące przez lata?
- 4-letnie opóźnienie jako mechanika (decyzje bez wsparcia)
- Budżet bandwidth (co wysłać z danych naukowych?)
- Ziemia jako coraz bardziej odległa, archaiczna "historia"
- Dylematy: poinformować o odkryciu teraz czy czekać na weryfikację?

### Kategoria F: KONTAKT Z ŻYCIEM
Jak modelujemy odkrycie życia w skali 0–6 (mikroby → inteligencja)?
- Jak budujemy napięcie wokół interpretacji biosygnatur?
- Mechanika kwarantanny i protokołów COSPAR
- Etyczne dylematy jako drzewka decyzji
- Różne endgame scenarios zależnie od poziomu życia

### Kategoria G: ZDARZENIA LOSOWE (Event System)
Jak projektujemy system eventów podczas rejsu?
- Tabela zagrożeń z researchu (promieniowanie, pył, awarie, konflikty)
- Narracyjne eventy RPG vs czyste mechaniki zarządcze
- Jak unikamy "grindu" i utrzymujemy napięcie przez lata misji

---

## FORMAT ODPOWIEDZI

Dla każdej kategorii (A–G) podaj:

```
## Kategoria X: NAZWA

### Wariant 1: [NAZWA] (Złożoność: Prosta)
**Opis**: [2-3 zdania co to jest]
**Jak działa**: [bullet points mechaniki]
**Uzasadnienie naukowe**: [skąd to wziąłeś z researchu]
**Plusy**: [co daje graczowi]
**Minusy / ryzyka**: [co może nie działać]
**Implementacja**: [1 zdanie jak to zrobić w TypeScript/JSON]

### Wariant 2: [NAZWA] (Złożoność: Średnia)
[...]

### Wariant 3: [NAZWA] (Złożoność: Zaawansowana)
[...]

**REKOMENDACJA**: Wariant X, bo [powód].
```

---

## PO ODPOWIEDZI

Użytkownik przejrzy propozycje i wybierze warianty dla każdej kategorii lub poprosi o modyfikacje. Dopiero po zatwierdzeniu mechanik przejdziemy do **PROMPT 02** — implementacji w plikach `.md` repo.

**Nie pisz kodu. Nie odwołuj się do plików repo. Skupiamy się wyłącznie na game design.**

---

*Research naukowy: patrz plik `00-RESEARCH-KONTEKST.md` dołączony do tej rozmowy.*
