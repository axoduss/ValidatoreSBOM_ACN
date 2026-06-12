# 🛡️ Validatore SBOM — Linee Guida ACN

## Descrizione
Il **Validatore SBOM** è un'applicazione web (single-page) progettata per verificare la conformità della Software Bill of Materials (SBOM) ai Criteri di Premialità stabiliti dal **DPCM 30 aprile 2025** e dalle **Linee Guida ACN** (Agenzia per la Cybersicurezza Nazionale).

Il tool supporta lo standard **CycloneDX 1.6** (Lista Tabellare 1, Livello 0+1) e verifica in modo automatico che i componenti e i servizi dichiarati provengano esclusivamente da Paesi ammessi dalla normativa.

## Funzionalità Principali
* **Validazione Strutturale:** Verifica la correttezza del formato base (es. `bomFormat` impostato su "CycloneDX", `specVersion` a 1.6) e la presenza di campi consigliati come `timestamp`, `tools`, `authors` e `manufacturer`.
* **Controllo Livello 0 (Oggetto della Fornitura):** Assicura la presenza e la validità dei metadati principali (`metadata.component`), inclusi nome, tipo e versione.
* **Controllo Livello 1 (Componenti e Servizi):** Analizza tutti i componenti e i servizi dichiarati, verificando la presenza dei campi obbligatori (nome, versione, produttore/provider). Gestisce anche le eccezioni per il software open-source senza entità organizzativa riconosciuta.
* **Verifica Geografica (Meccanismo On/Off):** Controlla il codice ISO 3166-1 del Paese di origine. Il punteggio premiale (8 punti) viene attribuito solo se tutti gli elementi provengono da Paesi ammessi (Paesi NATO, Paesi UE e Paesi dell'Allegato 3 del DPCM come Australia, Giappone, Svizzera, ecc.).
* **Esportazione Report:** Genera e permette di scaricare un report dettagliato della validazione in formato **HTML** o **JSON**.

## Come si usa
1. Apri l'applicazione nel tuo browser web.
2. Carica la tua SBOM scegliendo una delle due modalità disponibili:
   * **✏️ Incolla JSON:** Incolla direttamente il contenuto del file CycloneDX nell'apposita area di testo.
   * **📁 Carica File:** Trascina un file `.json` nell'area tratteggiata o clicca per selezionarlo dal tuo computer.
3. Clicca sul pulsante **"🔍 Valida SBOM"**.
4. Consulta la dashboard dei risultati, che include:
   * L'esito della conformità e il punteggio ottenuto.
   * Un riepilogo dei controlli superati, degli errori bloccanti e degli avvisi.
   * Tabelle di dettaglio per componenti, servizi e riepilogo della provenienza geografica.
5. Utilizza i pulsanti in basso per esportare il report nel formato desiderato.

## Tecnologie Utilizzate
Il progetto è realizzato in puro HTML, CSS e JavaScript (Vanilla). Non richiede alcun backend o dipendenza esterna, garantendo un'esecuzione rapida e sicura direttamente all'interno del browser dell'utente.