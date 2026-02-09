# 🛒 Lista Spesa — App Web Collaborativa

App web per gestire la lista della spesa da smartphone, con catalogo prodotti, ordinamento per corsia e sincronizzazione in tempo reale tra più persone.

## ✨ Funzionalità

- **Catalogo 279 prodotti** con ricerca e filtro per categoria
- **Gestione prodotti** — aggiungi, modifica, elimina prodotti con nome, corsia, prezzo, categoria e note
- **Lista dinamica** ordinata per corsia del supermercato
- **Tap per completare** — il prodotto sparisce dalla lista
- **📊 Statistiche** — storico spese, totale speso, media per spesa, prodotti più comprati, spesa per categoria
- **Autenticazione** — password per proteggere la lista, accesso tramite link + password
- **Collaborazione in tempo reale** — due persone vedono gli stessi aggiornamenti
- **Funziona offline** — come PWA installabile su smartphone
- **Zero costi** — hosting e database gratuiti

---

## 🚀 Setup in 10 minuti

### Passo 1: Crea un progetto Firebase (5 min)

1. Vai su [console.firebase.google.com](https://console.firebase.google.com/)
2. Accedi con il tuo account Google
3. Clicca **"Aggiungi progetto"** → nome: `lista-spesa` → Avanti → Avanti → Crea progetto
4. Nel menu a sinistra, clicca **"Creazione"** → **"Realtime Database"**
5. Clicca **"Crea database"**
6. Scegli la posizione più vicina (es. `europe-west1`) → **Avanti**
7. Seleziona **"Avvia in modalità test"** → **Abilita**

> ⚠️ La modalità test scade dopo 30 giorni. Vedi sotto per le regole permanenti.

8. Ora prendi la configurazione:
   - Clicca l'icona **⚙️ ingranaggio** in alto a sinistra → **Impostazioni progetto**
   - Scorri fino a **"Le tue app"** → clicca l'icona **`</>`** (Web)
   - Nome app: `spesa` → **Registra app**
   - Copia il blocco `firebaseConfig` che appare:

```javascript
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "lista-spesa-xxxxx.firebaseapp.com",
  databaseURL: "https://lista-spesa-xxxxx-default-rtdb.europe-west1.firebasedatabase.app",
  projectId: "lista-spesa-xxxxx",
  storageBucket: "lista-spesa-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

### Passo 2: Pubblica su GitHub Pages (5 min)

1. Vai su [github.com](https://github.com/) e accedi (o crea un account gratuito)
2. Clicca **"+"** in alto a destra → **"New repository"**
3. Nome: `lista-spesa` → **Public** → **Create repository**
4. Clicca **"uploading an existing file"**
5. Trascina i 4 file della cartella (`index.html`, `manifest.json`, `sw.js`, `README.md`)
6. Clicca **"Commit changes"**
7. Vai in **Settings** → **Pages** (nel menu a sinistra)
8. Source: **Deploy from a branch** → Branch: **main** → Cartella: **/ (root)** → **Save**
9. Aspetta 1-2 minuti, poi il tuo sito sarà online su:

```
https://TUOUSERNAME.github.io/lista-spesa/
```

### Passo 3: Configura Firebase nell'app (1 min)

1. Apri l'URL della tua app dal telefono
2. Tocca **⚙️** in alto a destra
3. Incolla la configurazione Firebase (il JSON tra le parentesi graffe)
4. Tocca **"Salva e Connetti"**
5. Lo stato cambierà da "📱 locale" a "🟢 sync"

### Passo 4: Condividi con l'altra persona (30 sec)

1. Tocca **📤** in alto a destra
2. Copia il link e invialo
3. L'altra persona apre il link e configura Firebase con la **stessa** configurazione
4. Ora siete sincronizzati! 🎉

---

## 📱 Come usare l'app

### A casa — Prepara la lista
1. Apri l'app → tab **Catalogo**
2. Cerca i prodotti o filtra per categoria
3. Tocca **+** per aggiungere (tocca più volte per aumentare la quantità)
4. Tocca **−** per rimuovere

### Al supermercato — Fai la spesa
1. Vai al tab **Lista**
2. I prodotti sono ordinati per corsia → segui il percorso!
3. Prodotto nel carrello? Tocca il **cerchio verde** → sparisce dalla lista
4. Lista vuota = spesa finita! ✅

### Nuova spesa
1. In fondo alla Lista, tocca **"🗑️ Svuota Lista"**

---

## 🔒 Regole di sicurezza Firebase (permanenti)

Dopo i primi 30 giorni, le regole di test scadono. Sostituiscile con queste nella console Firebase → Realtime Database → Regole:

```json
{
  "rules": {
    "lists": {
      "$listId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

Queste regole permettono lettura/scrittura solo a chi conosce l'ID della lista (che è un codice casuale nel link). Non è sicurezza "militare" ma è sufficiente per una lista della spesa.

Per maggiore sicurezza puoi aggiungere autenticazione anonima Firebase (gratuita).

---

## 🛠️ Personalizzazione

### Aggiungere prodotti
Apri `index.html`, cerca l'array `PRODUCTS` e aggiungi elementi:
```javascript
{id:"p279",n:"Nome Prodotto",a:"5",c:"Categoria",pr:2.50,no:"Note"},
```
- `a`: numero corsia, `"BF"` per Banco Frigo, `"BP"` per Banco Pesce, `""` per nessuna
- `c`: categoria (usa una esistente o creane una nuova)
- `pr`: prezzo indicativo
- `no`: note (marca, varianti, ecc.)

### Installare come app
Su iPhone: Safari → icona condivisione → "Aggiungi alla schermata Home"
Su Android: Chrome → menu ⋮ → "Aggiungi a schermata Home"

---

## 📄 Licenza
Uso personale gratuito. Creato con ❤️
