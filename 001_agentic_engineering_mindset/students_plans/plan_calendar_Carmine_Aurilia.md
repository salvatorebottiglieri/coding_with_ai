# Piano Webapp Coordinamento Riunioni

## 1. Goal ✅
Creare una web app che permetta ai dipendenti di una azienda di coordinare riunioni/meeting conciliando le diverse disponibilità. Il sistema aggregherà le preferenze e creerà automaticamente l'evento di calendario nel giorno con il massimo consenso (100% unanime).

---

## 2. Scope ✅
- ✅ Chiunque può creare una proposta di evento (coordinatore) con:
  - Titolo riunione
  - Descrizione
  - Slot orari candidati (giorno + ora)
  - Email dei destinatari (partecipanti)
- ✅ Ruoli incrociati: gli utenti possono essere sia organizzatori che partecipanti
- ✅ I partecipanti votano su gli slot compatibili con la loro disponibilità (possono votare sì solo su slot liberi per loro)
- ✅ I partecipanti possono cambiare il loro voto in qualsiasi momento fino a chiusura
- ✅ **Il primo slot che riceve il 100% di consenso viene sancito automaticamente**
- ✅ Il sondaggio si chiude automaticamente quando uno slot raggiunge il 100%
- ✅ Creazione automatica dell'evento di calendario sul calendario del coordinatore
- ✅ Email di notifica a tutti i partecipanti e al coordinatore con evento creato

**UI/UX:**
- ✅ Dashboard coordinatore: crea nuovo sondaggio, visualizza storico sondaggi aperti e chiusi
- ✅ Partecipante: link diretto al sondaggio specifico via email
- ✅ Votazione: slot visualizzati come card con checkbox per selezionare "sì"
- ✅ Riepilogo sondaggio: mostra stato, risultati parziali, link da condividere

---

## 3. Constraints ✅
- ✅ **Autenticazione partecipanti:** accesso open (no login), ma al completamento della votazione il partecipante deve inserire email, nome e cognome
- ✅ **Calendario:** integrazione con Google Calendar per la creazione degli eventi
- ✅ **Consenso unanime richiesto:** il primo slot con il 100% di voti viene automaticamente sancito
- ✅ **Fallback per stallo:** se dopo X giorni nessuno slot ha il 100%, il sistema notifica il coordinatore
- ✅ **Timeout configurabile:** il coordinatore può impostare per ogni evento quanti giorni attendere prima dell'avviso di stallo
- ✅ **Nessun limite di tempo per riproporre:** il coordinatore può riproporre nuovi slot in qualsiasi momento, senza vincoli temporali
- ✅ **Link validità:** sempre valido fino alla creazione dell'evento (chiusura sondaggio)
- ✅ **Fallback Google Calendar:** se creazione evento fallisce, email comunque inviata al coordinatore con dettagli
- ✅ **Sondaggio post-creazione:** completamente chiuso e inaccessibile dopo creazione evento

**Stack Tecnologico:**
- ✅ **Frontend:** React o Next.js
- ✅ **Backend:** Node.js + Express o Python + FastAPI
- ✅ **Database:** PostgreSQL
- ✅ **Deployment:** Cloud (AWS/Azure/GCP) con Docker
- ✅ **Integrazione Google Calendar:** libreria ufficiale Google API
- ✅ **Email:** servizio di notifica (es. SendGrid, AWS SES)

**MVP Priorità:**
- ✅ **Notifiche:** email (no real-time in-app per MVP)
- ✅ **Mobile:** fully responsive
- ✅ **Post-MVP:** analytics, real-time updates, multi-language, timezone handling, compliance GDPR, controllo conflitti calendario

---

## 4. User Stories ✅

**US1: Coordinatore crea una proposta di evento**
- Come coordinatore, voglio creare una proposta di riunione con titolo, descrizione, più slot orari candidati e lista di partecipanti
- Così che il sistema possa raccogliere le disponibilità e trovare lo slot migliore

**US2: Partecipante riceve invito e vota**
- Come partecipante, voglio ricevere un invito via email e accedere alla pagina di votazione
- Così che possa selezionare gli slot compatibili con la mia disponibilità

**US3: Partecipante cambia voto**
- Come partecipante, voglio poter cambiare il mio voto su uno slot in qualsiasi momento prima della chiusura
- Così che posso aggiornare la mia disponibilità se cambiano le circostanze

**US4: Sistema crea evento al 100% di consenso**
- Come sistema, quando uno slot raggiunge il 100% di voti, devo:
  - Chiudere automaticamente il sondaggio
  - Creare l'evento di calendario sul calendario del coordinatore
  - Inviare email di notifica al coordinatore e a tutti i partecipanti

**US5: Coordinatore riceve avviso di stallo**
- Come coordinatore, se dopo X giorni nessuno slot ha il 100%, voglio ricevere una notifica
- Così che posso riproporre nuovi slot se necessario

---

## 5. Acceptance Criteria ✅

**AC1: Votazione raggiunge il 100%**
- Dato: N partecipanti invitati a un evento
- Quando: uno slot riceve voti sì da tutti gli N partecipanti
- Allora: il sistema riconosce questo slot come "100% consenso" e procede all'automazione

**AC2: Sondaggio si chiude automaticamente**
- Quando: uno slot raggiunge il 100% di consenso
- Allora: il sondaggio viene chiuso, nessun altro voto è accettato, altre opzioni diventano inattive

**AC3: Evento viene creato su Google Calendar**
- Quando: sondaggio raggiunge il 100% su uno slot
- Allora: il sistema crea un evento su Google Calendar del coordinatore con:
  - Titolo: (titolo inserito dal coordinatore)
  - Descrizione: (descrizione inserita dal coordinatore)
  - Data e ora: (dello slot vincente)
  - Partecipanti: tutti gli invitati (se possibile aggiungere email nel calendar event)

**AC4: Notifiche inviate**
- Quando: evento viene creato
- Allora: email di notifica inviata a coordinatore e a tutti i partecipanti con dettagli dell'evento creato

**AC5: Nessuna votazione senza dati personali**
- Quando: partecipante completa la votazione
- Allora: viene richiesto di inserire email, nome, cognome prima di finalizzare
- E: il voto non è conteggiato finché dati non sono forniti

**AC6: Avviso di stallo inviato**
- Quando: X giorni passano senza raggiungere il 100% su nessuno slot (X configurabile dal coordinatore)
- Allora: email di avviso inviata al coordinatore invitandolo a riproporre nuovi slot

---

## 6. Risks ✅

**R1: Integrazione Google Calendar fallisce**
- Rischio: Il consenso 100% è raggiunto, ma la creazione dell'evento su Google Calendar fallisce
- Mitigazione: Email inviata comunque al coordinatore con messaggio di errore e dettagli dell'evento da creare manualmente
- Mitigazione: Il sondaggio rimane in stato "pending" finché l'evento non è creato con successo

**R2: Partecipante accede link dopo evento creato**
- Rischio: Partecipante clicca link dopo la chiusura del sondaggio e vede interfaccia confusa
- Mitigazione: Sondaggio è completamente chiuso e inaccessibile; partecipante vede messaggio "Questo sondaggio è stato concluso"

**R3: Link di partecipazione rimane valido troppo a lungo**
- Rischio: Partecipante riceve link ma lo usa settimane dopo, quando il coordinatore ha già rilanciato con nuovi slot
- Mitigazione: Link è valido finché il sondaggio è aperto (finché non viene creato l'evento)

**R4: Assenza di verifica email valida**
- Rischio: Spam o voti non validi da email non verificate
- Mitigazione: Implementare validazione SMTP per confermare che l'email sia attiva

**R5: Partecipante non riceve email di invito (spam, bounce)**
- Rischio: Partecipante non è consapevole del sondaggio e non vota
- Mitigazione: Coordinatore può reinviare inviti manuali; link rimane valido

**R6: Sincronizzazione orari in timezone diverse**
- Rischio: Coordinatore e partecipanti in timezone diverse, creazione evento con ora sbagliata
- Mitigazione: (Da definire se necessario: sistema di timezone o conferma manuale dell'orario?)
