## 8. Checklist TODO Completa (per Sviluppo Reale)

Questa sezione aggrega tutte le attività TODO identificate nelle sezioni precedenti, fornendo una checklist completa per lo sviluppo del progetto.

### 8.1 Contesto e Principi

*   [x] Verificare la coerenza dei principi con l'implementazione effettiva.
*   [ ] Documentare eventuali deviazioni dai principi per giustificarle.

### 8.2 Architettura Modulare

*   [x] Definire la struttura dettagliata dei moduli UI (`src/`).
    *   `src/nome-app/index.jsx|tsx` (entry point)
    *   `src/nome-app/components/` (componenti specifici dell'app)
    *   `src/nome-app/hooks/` (custom hooks specifici dell'app)
    *   `src/nome-app/types/` (tipi specifici dell'app, per TS)
    *   `src/nome-app/utils/` (utility specifiche dell'app)
    *   Utilizzo di hooks e utility globali da `src/` root.

*   [x] Implementare il processo di build e verifica degli asset in `assets/` (generazione assets via `pnpm build` con `BASE_URLe=.`).
*   [x] **MIGRAZIONE**: Sostituire `hoffmann_server_python` con `mcp-server-motherduck` (nella root del progetto).
*   [x] Porting della logica e-commerce (tool, entità) nel nuovo server `mcp-server-motherduck`.
*   [x] Creare il primo prototipo del "Vertical Profile" e un meccanismo per la sua lettura (`config_loader.py` portato in `mcp_server_motherduck`).
*   [x] Individuare e documentare il database per la produzione (MotherDuck).
*   [x] Aggiornare `README.md` (in `sdk-app`) con le istruzioni per l'avvio e la configurazione del nuovo progetto.

### 8.3 Schema Dati Minimo

*   [x] Finalizzare lo schema dati per le entità principali, includendo tutti i campi necessari (Schema MotherDuck consolidato).
*   [x] Definire un esempio di "Vertical Profile" per il vertical "Vestiti" in `mcp-server-motherduck/src/mcp_server_motherduck/vertical_profile.json`.
*   [x] Implementare i modelli dati nel backend (`hoffmann_store.py`) in modo da supportare lo schema definito e gli attributi dinamici.
*   [x] Rimuovere script di seeding obsoleti (`data/` e `update_product_images.py` rimossi).

### 8.4 Design del Layer MCP

*   [x] Definire gli schemi JSON per l'input e l'output di ogni tool elencato.
*   [x] Implementare i stub per i tool nel server MCP (`hoffmann_tools.py`).
*   [x] Integrare la gestione di `widgetSessionId` e `widgetState` (supporto base nei tool).
*   [x] Abilitare `CallToolResult` e payload `_meta` (`openai/outputTemplate`) in `hoffmann_tools.py` per il rendering dei widget.
*   [x] **Gestione Immagini**: Implementare endpoint HTTP dedicato per servire le immagini (URL invece di base64) per compatibilità con i widget. (RISOLTO: Uso di GitHub Raw URLs).
*   [x] **Tool Immagini**: Esporre funzionalità/tool per il parsing o recupero corretto delle immagini per ChatGPT. (RISOLTO: `hoffmann_store.py` gestisce `image_url`).
*   [x] Creare o adattare i componenti UI (`src/`) per rispondere ai diversi `outputTemplate` e `widgetState`. (ATTIVO: `hoffmann-carousel` abilitato).

### 8.5 Strategia di Deploy su Render

*   [x] Configurare il server `mcp-server-motherduck` per servire i file statici delle app dalla directory `sdk-app/assets` (mounted su `/assets` in `__init__.py`).
*   [x] Assicurarsi che il server utilizzi `0.0.0.0` e `os.environ.get("PORT")` (supportato da `uvicorn` e entry point `main`).
*   [x] Aggiornare le istruzioni di deploy nel `README.md`.

### 8.6 Procedura di Collegamento in ChatGPT

*   [ ] Documentare la procedura esatta per configurare il connettore in ChatGPT (Settings > Connectors).
*   [ ] Testare il collegamento con un server MCP locale esposto tramite `ngrok`.
*   [ ] Testare il collegamento con il server MCP deployato su Render.

### 8.7 Roadmap in Milestone

*   [ ] Definire metriche di successo per ogni milestone.
*   [ ] Assegnare priorità e stimare tempi per i task di ogni milestone.
*   [ ] Allineare la roadmap con le esigenze di business e gli stakeholder.

### 8.8 Documentazione e Testing

*   [x] **Documentazione**: `README.md` aggiornato per riflettere la migrazione al server unificato.
*   [x] **Testing Minimale**: Script `verify_server.py` creato e testato per la verifica dei tool.
*   [x] **Refactoring e Pulizia**: Rimossa cartella `hoffmann_server_python`, pulita root `sdk-app`.
