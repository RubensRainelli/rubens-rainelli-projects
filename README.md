# Rubens Rainelli - Projects Directory

Benvenuti nel repository indice dei miei progetti personali. Questa directory ospita un elenco curato dei miei lavori pubblici di sviluppo software, utility e specifiche.

L'applicazione è strutturata come una Single Page Application (SPA) ultra-leggera in puro stile **Cyberpunk** con supporto multilingua (Italiano e Inglese) basato sul rilevamento automatico del browser.

---

## 🔗 Live Demo / Link Pubblico

Puoi visualizzare l'indice dei progetti interattivo direttamente online al seguente indirizzo:

👉 **[Live Index (Official Link)](https://github.io/RubensRainelli/rubens-rainelli-projects/rubensrainelli-projects.html)**
*(Nota: L'indirizzo standard di GitHub Pages per questa pagina è [https://rubensrainelli.github.io/rubens-rainelli-projects/rubensrainelli-projects.html](https://rubensrainelli.github.io/rubens-rainelli-projects/rubensrainelli-projects.html))*

---

## 🛠 Struttura del Progetto

Il progetto è composto dai seguenti moduli:

- **`projects.json`**: Il database centralizzato contenente le informazioni relative a ciascun progetto in formato multilingua (`it` ed `en`):
  - Nome del progetto
  - Descrizione del progetto
  - Collegamento all'immagine illustrativa
  - Link al codice sorgente del progetto (GitHub)
  - Link pubblico per provarlo/installarlo (se disponibile)
  - Stato di attività (`active` flag: `true` per progetti attivi, `false` per progetti dismessi)
- **`rubensrainelli-projects.html`**: Il motore frontend della SPA. Esegue il rilevamento automatico della lingua dell'utente (con fallback manuale ed overlay di prima scelta), gestisce i filtri di ricerca testuale e di stato (tutti, attivi, dismessi) ed effettua il rendering dinamico delle schede.
- **`style.css`**: Il foglio di stile con design token Cyberpunk ad alta saturazione, animazioni di scansione e glitch testuali, scrollbar ottimizzata e layout responsivo.
- **`images/`**: Icone e illustrazioni vettoriali (SVG) personalizzate per ciascun progetto integrato nel portfolio.

---

## 🗂 Progetti Inclusi

1. **PEFL License Specification**: Specifica e testi della licenza PEFL (progetto-centrica).
2. **Linux Dependency Guide**: Strumento offline-first per l'auditing, migrazione e mappatura delle dipendenze di sistema Linux.
3. **MyCard**: SPA standalone offline-first per salvare e generare carte fedeltà, codici fiscali e codici QR.
4. **Gemini CLI Reader**: Visualizzatore locale di log e cronologia delle sessioni per Gemini CLI.
5. **AEM Enhancer**: Estensione Chrome per velocizzare il flusso di lavoro degli sviluppatori e autori in Adobe Experience Manager (AEM).
6. **Adobe Case-Sensitive Volumes Workaround**: Libreria e hack per aggirare i controlli dei volumi case-sensitive nell'installer Adobe CC su macOS.

---

## 💻 Sviluppo e Modifiche Locali

Per testare o aggiungere nuovi progetti al database locale:

1. Modifica la lista all'interno di `projects.json`.
2. Aggiungi eventuali nuove risorse visuali o loghi nella directory `images/`.
3. Apri localmente `rubensrainelli-projects.html` direttamente nel tuo browser o esegui un server HTTP locale:
   ```bash
   # Utilizzando python
   python3 -m http.server 8000
   ```
4. Naviga su `http://localhost:8000/rubensrainelli-projects.html`.
