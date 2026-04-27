# ANG Documenti Cantieri 📁

PWA per la gestione documentale dei cantieri fotovoltaici.  
Estensione di **ANG Gestione Cantieri** — stesso Supabase, stessa autenticazione.

---

## 🚀 Deploy su GitHub Pages

1. **Crea un nuovo repository** su GitHub (es. `athena-documenti`)
2. **Carica i file** di questa cartella nel repository
3. Vai su **Settings → Pages → Deploy from branch → main / root**
4. L'app sarà disponibile su `https://marcogiffi-a11y.github.io/athena-documenti/`

---

## 🔧 Configurazione obbligatoria

### 1. Supabase Anon Key
In `index.html`, cerca la riga:
```js
const SUPABASE_ANON_KEY = 'INSERISCI_QUI_LA_TUA_ANON_KEY';
```
Sostituisci con la tua anon key da:  
**Supabase Dashboard → Settings → API → `anon public`**

### 2. Storage Bucket
Crea un bucket **`documenti`** con accesso **Public**:  
Supabase Dashboard → Storage → New bucket → Nome: `documenti` → Public: ✅

### 3. Tabella DB
Esegui lo script `supabase-setup.sql` nell'editor SQL di Supabase.

---

## 📱 Funzionalità

| Feature | Descrizione |
|---|---|
| 🔐 Login duale | Admin (PIN 1507) o Squadra (codice ANG-XXXX) |
| 📋 Lista cantieri | Recupera i cantieri dal DB condiviso |
| 📁 Fasi documento | Progettazione · Autorizzazioni · Installazione · Collaudo |
| 📷 Scatta foto | Usa la fotocamera del telefono |
| 📎 Carica file | PDF, foto, documenti vari |
| 📑 Scan → PDF | Foto multiple unite in un PDF A4 scaricabile |
| 👷 Permessi | Squadra vede solo i propri cantieri |
| ➕ Nuovo cantiere | Solo admin può aggiungere cantieri |
| 📲 PWA | Installabile come app su iOS e Android |

---

## 🗄️ Schema DB

```
cantieri          ← tabella esistente (condivisa con ANG Cantieri)
squadre           ← tabella esistente (condivisa con ANG Cantieri)
assegnazioni_cantieri ← nuova (se non già presente)
documenti_cantiere    ← nuova
```

---

## 🎨 Stack

- **React 18** via CDN (no build step)
- **Supabase JS v2** — DB + Storage real-time
- **jsPDF** — generazione PDF da foto
- **Font**: Oswald + JetBrains Mono + Barlow
- **Tema**: Dark industrial con accent ambra
