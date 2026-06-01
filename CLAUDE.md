# CLAUDE.md

Guida per Claude Code su questo repository.

## Progetto
**Lista Spesa** — PWA (web app) per la lista della spesa collaborativa.
- L'app è interamente in **`index.html`** (HTML + CSS + JS inline, niente build step).
- `manifest.json` e `sw.js` completano la PWA; `sw.js` fa caching network-first.
- Persistenza: **Firebase Realtime Database** se configurato, altrimenti **localStorage** (modalità locale).
- Hosting statico (GitHub Pages). Nessun backend.

## Convenzioni

### Versione app — INCREMENTARE A OGNI NUOVA PR
A **ogni nuova PR** incrementare la costante `APP_VERSION` in `index.html`
(mostrata in fondo al pannello ⚙️ Impostazioni).
- Default: incremento di **patch** (es. `1.0.7` → `1.0.8`).
- Incremento **minor** (es. `1.1.0`) per funzionalità rilevanti.
- Includere il bump nello stesso branch/PR della modifica.

### Workflow Git
- Sviluppo su branch `claude/<descrizione>`, PR verso `main`.
- Non aprire una PR se non richiesto esplicitamente.

## Verifiche
- Lo script JS è inline in `index.html`. Per un controllo sintattico veloce:
  estrarre il blocco `<script>` più lungo e lanciare `node --check`.
