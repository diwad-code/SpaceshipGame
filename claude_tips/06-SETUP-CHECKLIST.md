# Setup Checklist — Sprint 0

> Wykonaj WSZYSTKO z tej listy ZANIM napiszesz pierwszą linię kodu gry. Zajmie ~2-4h za pierwszym razem (głównie pobieranie i instalacje).

## A. Konta i subskrypcje

- [ ] **Konto GitHub** (jeśli nie masz): https://github.com/signup
- [ ] **GitHub Copilot Pro+**: https://github.com/features/copilot/plans
  - $39/mies, 1500 premium requests, dostęp do GPT-5.x, Claude Sonnet/Opus, Gemini
  - **Ostrzeżenie**: rejestracje czasem wstrzymane, sprawdź aktualność
  - **Plan B**: zwykłe Pro ($10/mies) wystarczy na start
- [ ] **Konto Google Play Developer**: https://play.google.com/console
  - **$25 jednorazowo** (verified)
  - Załatw teraz — weryfikacja konta zajmuje czasem dni
  - Potrzebne dopiero do publikacji APK, ale procedura długa
- [ ] **Konto Cloudflare** (free): https://dash.cloudflare.com/sign-up
  - Do hostingu Cloudflare Pages — najprostszy darmowy hosting
- [ ] **Konto OpenAI ChatGPT Plus** ($20/mies): https://chat.openai.com
  - Do ChatGPT Projects z mentorem (master prompt)
  - **Plan B**: Claude Pro ($20/mies) działa równie dobrze, ale w innym ekosystemie

## B. Narzędzia developerskie

### Niezbędne (zainstaluj w tej kolejności)

- [ ] **Node.js LTS** (wersja 22.x lub nowsza): https://nodejs.org
  - Sprawdź po instalacji w terminalu: `node --version` → powinno pokazać `v22.x.x`
  - npm instaluje się razem
- [ ] **Git** (system kontroli wersji): https://git-scm.com/downloads
  - Przy instalacji na Windows: zaznacz "Git from command line and 3rd party tools"
  - Sprawdź: `git --version`
- [ ] **VS Code**: https://code.visualstudio.com
- [ ] **Java JDK 17** (potrzebne dla Bubblewrap): https://adoptium.net/temurin/releases/?version=17
  - Wybierz: Temurin 17 (LTS), Windows x64, .msi
  - Sprawdź: `java -version` → powinno pokazać `openjdk version "17.x.x"`
- [ ] **Android Studio** (potrzebne dla Bubblewrap, ~5 GB): https://developer.android.com/studio
  - Pierwsza instalacja zajmie godzinę i pobierze SDK
  - **Możesz to odłożyć do Sprintu 6** (Bubblewrap), ale lepiej mieć zainstalowane na zapas

### Edytor pixel art (wybierz jeden)

- [ ] **Pixelorama** (free, open source): https://orama-interactive.itch.io/pixelorama
  - Najlepszy darmowy. Polecany na start.
- [ ] **Aseprite** ($19.99 na Steam): https://store.steampowered.com/app/431730/Aseprite
  - Branżowy standard. Kup gdy zaczniesz robić własne animacje.
- [ ] **Piskel** (browser, zero install): https://www.piskelapp.com
  - Do super-szybkich szkiców i prostych eksperymentów.

## C. Rozszerzenia VS Code

Otwórz VS Code → Extensions (`Ctrl+Shift+X`) → zainstaluj kolejno:

- [ ] **GitHub Copilot** (`GitHub.copilot`)
- [ ] **GitHub Copilot Chat** (`GitHub.copilot-chat`)
- [ ] **ESLint** (`dbaeumer.vscode-eslint`) — łapie błędy stylu i bugi
- [ ] **Prettier - Code formatter** (`esbenp.prettier-vscode`) — auto-format on save
- [ ] **Error Lens** (`usernamehw.errorlens`) — błędy pokazane inline, **kluczowe dla początkującego**
- [ ] **GitLens** (`eamodio.gitlens`) — historia zmian inline
- [ ] **Path Intellisense** (`christian-kohler.path-intellisense`) — autocomplete ścieżek
- [ ] **TODO Tree** (`Gruntfuggly.todo-tree`) — lista wszystkich `// TODO:` w projekcie
- [ ] **Live Preview** (`ms-vscode.live-server`) — podgląd HTML w side-panel

### Konfiguracja VS Code (User Settings)

Otwórz `Ctrl+,` → kliknij ikonkę „Open Settings (JSON)" w prawym górnym → wklej:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "files.autoSave": "onFocusChange",
  "files.eol": "\n",
  "typescript.preferences.quoteStyle": "single",
  "typescript.updateImportsOnFileMove.enabled": "always",
  "github.copilot.enable": {
    "*": true,
    "markdown": true,
    "plaintext": false
  },
  "errorLens.enabledDiagnosticLevels": ["error", "warning"]
}
```

## D. Pierwszy projekt — sprawdź czy wszystko działa

W terminalu (PowerShell na Windows / Terminal na Mac):

```bash
# 1. Wybierz folder roboczy (np. Documents/Projects)
cd Documents/Projects

# 2. Sklonuj oficjalny template Phasera
npx degit phaserjs/template-vite-ts star-search

# 3. Wejdź do folderu
cd star-search

# 4. Zainstaluj zależności
npm install

# 5. Uruchom dev server
npm run dev
```

**Definicja „done"**: 
- Otwórz przeglądarkę na `http://localhost:5173`
- Powinieneś zobaczyć przykładową scenę Phasera (logo, animacja)
- Brak czerwonych błędów w terminalu

Jeśli to działa — **gratulacje, środowisko gotowe**. Możesz przejść do Sprintu 1.

## E. Repozytorium na GitHubie

```bash
# Wewnątrz folderu star-search
git init
git add .
git commit -m "chore: initial commit from phaser template"

# Stwórz repo na github.com/new (puste, bez README)
# Potem:
git remote add origin https://github.com/<twoja-nazwa>/star-search.git
git branch -M main
git push -u origin main
```

## F. Hosting na Cloudflare Pages (5 minut)

1. Wejdź na https://dash.cloudflare.com → **Pages** → **Create a project** → **Connect to Git**
2. Połącz z GitHubem, wybierz repo `star-search`
3. Build settings:
   - Framework preset: **Vite**
   - Build command: `npm run build`
   - Build output directory: `dist`
4. **Save and Deploy**

**Definicja „done"**: Cloudflare wygeneruje URL typu `star-search-abc.pages.dev`. Otwórz — powinieneś zobaczyć tę samą grę co lokalnie.

## G. Pakiety pixel art (zob. `07-ASSETS-LIST.md`)

Pobierz minimum:
- [ ] Kenney – Space Shooter Redux
- [ ] Kenney – UI Pack
- [ ] Kenney – Input Prompts Pixel 16x

Wrzuć do `public/assets/kenney/<paczka-name>/` w projekcie.

## H. Pliki konfiguracyjne projektu (skopiuj z paczki)

- [ ] Skopiuj `02-COPILOT-INSTRUCTIONS.md` → `.github/copilot-instructions.md`
- [ ] Skopiuj `03-PROMPT-NEW-EVENT.md` → `.github/prompts/new-event.prompt.md`
- [ ] Skopiuj `04-PROMPT-NEW-SCENE.md` → `.github/prompts/new-scene.prompt.md`
- [ ] Skopiuj `05-PROMPT-CODE-REVIEW.md` → `.github/prompts/code-review.prompt.md`
- [ ] Stwórz `docs/SCOPE.md` z listą feature'ów MVP (z `01-PROJECT-PLAN.md`)
- [ ] Stwórz `docs/IDEAS_LATER.md` (pusty na start)

## I. Mentor GPT-5.4

- [ ] W ChatGPT: **New Project** → nazwa: „Star Search Mentor"
- [ ] Wklej `00-MASTER-PROMPT-GPT.md` w **Custom Instructions** Projektu
- [ ] Załącz `01-PROJECT-PLAN.md` jako plik wiedzy w Projekcie
- [ ] Pierwszy test: napisz „Cześć, jestem na Sprincie 0, czy wszystko gotowe?" — powinien sprawdzić checklistę i pochwalić.

---

## Status — odhaczaj jak idziesz

```
[ ] Sekcja A — Konta            (zajmie 30 min, czeka na weryfikacje)
[ ] Sekcja B — Narzędzia         (zajmie 1-2h, głównie pobieranie)
[ ] Sekcja C — VS Code           (zajmie 15 min)
[ ] Sekcja D — Pierwszy projekt  (zajmie 10 min, jeśli wszystko OK)
[ ] Sekcja E — GitHub repo       (zajmie 10 min)
[ ] Sekcja F — Cloudflare Pages  (zajmie 10 min)
[ ] Sekcja G — Pixel art assety  (zajmie 20 min)
[ ] Sekcja H — Pliki projektu    (zajmie 10 min)
[ ] Sekcja I — Mentor GPT        (zajmie 10 min)
```

**Wszystko odhaczone? Idź do `09-ROADMAPA-SPRINTOW.md`, Sprint 1.**
