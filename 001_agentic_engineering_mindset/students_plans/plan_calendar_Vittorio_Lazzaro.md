# Piano di sviluppo: App Pianificazione Eventi con Consenso

## 1. Goal ✅
Costruire un'app di pianificazione eventi basata su consenso dove:
- Chiunque può proporre orari per un evento
- Le proposte possono essere riservate a persone con tag specifici
- I partecipanti hanno un limite di tempo per rispondere
- L'evento si chiude automaticamente quando tutti hanno risposto
- Se durante il sondaggio viene raggiunta una percentuale di consenso (opzionale, 1-100%), l'evento si chiude automaticamente
- La percentuale di consenso calcola il rapporto tra voti positivi e totale dei partecipanti (inclusi chi non ha ancora risposto)
- Al termine del sondaggio, se non c'è consenso, il creatore sceglie tra: maggioranza, annullare, o rischedulare
- Gli eventi sono salvati localmente in CSV con architettura estensibile per future integrazioni di sistemi esterni

## 2. Scope ✅
**In:**
- Sistema di creazione e gestione utenze (semplice)
- Sistema di creazione eventi con parametri: tag, limite di tempo, orari proposti, percentuale di consenso (opzionale)
- Sistema di votazione con chiusura automatica (tutti rispondono o percentuale raggiunta)
- Sistema di fallback con scelta del creatore
- Persistenza locale in CSV
- Web app con Flask

**Out (futuri):**
- Integrazioni con calendari esterni
- Notifiche email/push

## 3. Constraints ✅
- Stack: Python + Flask
- Persistenza: CSV (struttura normalizzata in 4 file)
  - users.csv (id, username, tag)
  - events.csv (id, creatore, titolo, deadline, percentuale_consenso, stato)
  - proposals.csv (id_evento, id_proponente, orario, tag_riservato)
  - votes.csv (id_evento, id_utente, id_orario, voto, timestamp)
- Solo chi ha il tag specifico può visualizzare, votare e proporre orari per quell'evento
- L'organizzatore deve avere il tag per creare l'evento
- Nuovi orari proposti durante il sondaggio vengono aggiunti subito
- La deadline rimane fissa anche se vengono proposte nuove opzioni

## 4. User Stories ✅
- **US1 (Organizzatore):** Creo un evento specificando titolo, tag, deadline, orari iniziali e percentuale di consenso (opzionale)
- **US2 (Organizzatore):** Visualizzo il sondaggio in tempo reale e vedo i voti mentre arrivano
- **US3 (Partecipante):** Accedo ai sondaggi per i tag che possiedo
- **US4 (Partecipante):** Voto gli orari proposti
- **US5 (Partecipante):** Propongo nuovi orari durante il sondaggio
- **US6 (Sistema):** Il sondaggio si chiude automaticamente quando tutti hanno votato oppure quando la percentuale di consenso è raggiunta
- **US7 (Organizzatore):** Se il sondaggio termina senza consenso, scelgo tra: maggioranza, annullare, o rischedulare

## 5. Acceptance Criteria ✅
- **US1:** L'evento è salvato in events.csv con id univoco, le proposte iniziali sono in proposals.csv, solo utenti con tag specifico lo vedono, timer inizia subito
- **US2:** L'organizzatore visualizza sondaggio in real-time con conteggio voti per ogni orario
- **US3:** Partecipante accede solo ai sondaggi del tag che possiede
- **US4:** Voto viene registrato in votes.csv con timestamp
- **US5:** Nuovo orario appare subito nel sondaggio per chi ha il tag, è votabile da tutti i partecipanti
- **US6:** Sondaggio si chiude quando: (a) tutti i partecipanti hanno votato, oppure (b) un orario raggiunge la percentuale di consenso calcolata su TUTTI i partecipanti (inclusi non votanti)
- **US7:** Organizzatore riceve prompt con 3 opzioni: maggioranza, annullare, rischedulare. Fallback "maggioranza" = orario con più voti "sì" in assoluto

## 6. Risks ✅
- **Risk 1:** Cosa succede se due orari hanno lo stesso numero di voti "sì"? → Mitigazione: scegli l'orario proposto per primo (timestamp più vecchio)
- **Risk 2:** Cosa succede se nessun orario ha voti "sì"? → Mitigazione: organizzatore deve scegliere rischedulare o annullare, non può usare fallback "maggioranza"
- **Risk 3:** Un partecipante potrebbe non votare mai → Mitigazione: il sondaggio chiude comunque alla deadline, i non-votanti non influenzano il risultato finale