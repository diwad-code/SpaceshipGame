# Star Search — Pakiet startowy projektu

Witaj w pakiecie startowym dla gry **Star Search** — retro pixel-art space management game (PWA + Android APK).

## Co jest w paczce

| Plik | Co to jest | Kiedy używać |
|---|---|---|
| `00-MASTER-PROMPT-GPT.md` | **Custom instructions dla GPT-5.4** w ChatGPT Project | Wklej do Custom Instructions w nowym Projekcie ChatGPT |
| `01-PROJECT-PLAN.md` | Cały plan techniczny, stack, roadmapa | Czytaj w razie wątpliwości, wklej GPT jako kontekst |
| `02-COPILOT-INSTRUCTIONS.md` | Instrukcje dla GitHub Copilot | Skopiuj jako `.github/copilot-instructions.md` w repo |
| `03-PROMPT-NEW-EVENT.md` | Slash-command Copilota: dodawanie zdarzeń | Skopiuj jako `.github/prompts/new-event.prompt.md` |
| `04-PROMPT-NEW-SCENE.md` | Slash-command Copilota: nowa scena Phasera | Skopiuj jako `.github/prompts/new-scene.prompt.md` |
| `05-PROMPT-CODE-REVIEW.md` | Slash-command Copilota: code review | Skopiuj jako `.github/prompts/code-review.prompt.md` |
| `06-SETUP-CHECKLIST.md` | Checklist co zainstalować, krok po kroku | Wykonaj PRZED rozpoczęciem projektu |
| `07-ASSETS-LIST.md` | Linki do paczek pixel art do pobrania | Pobierz przed sprintem 1 |
| `08-CAVEATS.md` | Pułapki i ryzyka, na co uważać | Przeczytaj raz, wracaj gdy coś idzie źle |
| `09-ROADMAPA-SPRINTOW.md` | Plan tygodniowy sprintów do MVP | Trzymaj otwarte, odhaczaj zadania |

## Jak zacząć (5 minut)

1. **Otwórz `06-SETUP-CHECKLIST.md`** i przejdź przez instalacje (Node.js, VS Code, Git, Android Studio + JDK).
2. **Otwórz ChatGPT**, stwórz nowy Project o nazwie „Star Search Mentor".
3. **Wklej zawartość `00-MASTER-PROMPT-GPT.md`** w Custom Instructions tego Projektu.
4. **Stwórz repo na GitHubie** (np. `star-search`) i sklonuj je lokalnie.
5. **Skopiuj pliki 02–05** do odpowiednich miejsc w repo (zobacz tabelę wyżej).
6. **Pierwsza wiadomość do GPT**: „Cześć, mam wszystko z pakietu startowego. Zacznijmy od Sprintu 0 — przeprowadź mnie przez setup projektu."

## Stack — w skrócie

- **Phaser 3** (NIE Phaser 4) + **TypeScript** + **Vite**
- Template: `phaserjs/template-vite-ts`
- PWA przez `vite-plugin-pwa` (Workbox)
- Storage: IndexedDB przez `idb-keyval`
- Hosting: **Cloudflare Pages**
- Android APK: **Bubblewrap** (Trusted Web Activity) lub **PWA Builder** (graficznie)

## Zasady żelazne (przeczytaj raz, pamiętaj zawsze)

1. **MVP > perfekcja**. Pierwsza wersja ma być brzydka i działać, a nie ładna i nigdy nie wydana.
2. **Nie dodawaj nowych bibliotek** poza zatwierdzonym stackiem bez świadomej decyzji.
3. **Codziennie testuj na realnym Androidzie**, nie tylko w przeglądarce desktop.
4. **W piątek każdego sprintu MUSI być coś klikalnego.** Bez wyjątku.
5. **Idee na później idą do `IDEAS_LATER.md`**, nie do kodu.

---

*Pakiet wygenerowany na podstawie researchu (maj 2026). Wszystkie wersje bibliotek i tools — sprawdzaj aktualność w momencie startu projektu.*
