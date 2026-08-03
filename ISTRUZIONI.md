# Pubblicazione su GitHub Pages — App Segnalazioni Gruppo CER

Questa cartella contiene tutto il necessario per pubblicare l'app come sito web
pubblico, apribile da qualsiasi cellulare senza login e senza account Claude.

## Contenuto della cartella

- `index.html` — l'app completa (React + jsPDF caricati da CDN, nessuna build necessaria)
- `manifest.json` — configurazione per l'installazione come app ("Aggiungi a schermata Home")
- `sw.js` — service worker per il funzionamento offline
- `icon-192.png` / `icon-512.png` — icone dell'app
- `ISTRUZIONI.md` — questo file

Tutti i file devono stare nella **stessa cartella**, allo stesso livello.

## Pubblicazione (procedura, ~10 minuti)

### 1. Crea il repository
1. Vai su github.com e accedi (o crea un account gratuito).
2. In alto a destra: **New repository**.
3. Nome, ad esempio: `segnalazioni-cer`.
4. Imposta **Public** (necessario per GitHub Pages nel piano gratuito).
5. **Create repository**.

### 2. Carica i file
1. Nella pagina del repo appena creato: **Add file → Upload files**.
2. Trascina TUTTI i file di questa cartella (index.html, manifest.json, sw.js,
   le due icone). NON caricare questo ISTRUZIONI.md se non vuoi (è opzionale).
3. In basso: **Commit changes**.

### 3. Attiva GitHub Pages
1. Nel repo, apri **Settings** (in alto).
2. Menu a sinistra: **Pages**.
3. Sotto "Build and deployment", voce **Source**: scegli **Deploy from a branch**.
4. In **Branch** seleziona `main` e cartella `/ (root)`, poi **Save**.
5. Attendi 1–2 minuti: in cima alla pagina comparirà il link pubblico, del tipo:
   `https://TUONOME.github.io/segnalazioni-cer/`

Quello è il link da distribuire agli utenti esterni.

## Distribuzione agli utenti

- Invia il link via WhatsApp/email, oppure genera un **QR code** dal link
  (qualsiasi generatore online) da stampare o affiggere.
- Al primo accesso, su smartphone l'utente può installarla:
  - **Android (Chrome):** menu ⋮ → "Aggiungi a schermata Home" / "Installa app".
  - **iPhone (Safari):** icona Condividi → "Aggiungi a Home".
- Da quel momento si apre come un'app, a schermo intero, e funziona anche offline.

## Come funziona per l'utente

1. Apre l'app → **Nuova segnalazione**.
2. Sceglie l'ambito (Sicurezza / Guasto-Logistica), compila i passi, può
   aggiungere foto e posizione.
3. Tocca **Genera PDF**: il documento viene creato sul telefono.
4. Tocca **Condividi su WhatsApp**: si apre il menu di condivisione con il PDF
   già allegato; sceglie il contatto/gruppo giusto e invia.

Nota: per motivi di sicurezza WhatsApp non consente di preselezionare via web il
destinatario. L'utente sceglie il contatto al momento dell'invio. Il testo di
condivisione ricorda già a quale ufficio inoltrare in base alla categoria.

## Aggiornamenti futuri

Per modificare l'app (testi, categorie, tipi di segnalazione) basta modificare
`index.html` nel repo (**Edit** dalla matita di GitHub) e fare commit: il sito si
aggiorna da solo in un paio di minuti. Se hai aggiornato il service worker,
cambia il numero di versione in `sw.js` (riga `const CACHE = "...v1"` → `v2`) per
forzare il refresh della cache sui dispositivi.

## Note importanti

- **Connessione:** serve internet solo al primo caricamento (per scaricare le
  librerie dai CDN) e al momento dell'invio WhatsApp. La compilazione e la
  generazione del PDF funzionano anche offline una volta aperta l'app.
- **Privacy/GDPR:** l'app non invia dati a nessun server; il PDF resta sul
  dispositivo finché l'utente non lo condivide. Nella schermata iniziale è
  presente una nota informativa di base: valuta con il titolare del trattamento
  se integrarla con l'informativa completa.
- **Nessun costo:** GitHub Pages e i CDN usati sono gratuiti.
