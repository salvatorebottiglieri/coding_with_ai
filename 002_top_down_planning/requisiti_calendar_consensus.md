# Calendar Consensus App — Requisiti

Un'applicazione web che automatizza la creazione di eventi di calendario solo quando tutti
i partecipanti sono d'accordo sulla stessa data e orario.

---

## 1. Descrizione Generale

Coordinare una riunione tra più persone richiede scambi di messaggi, negoziazioni su orari,
e continui follow-up. L'app risolve questo problema: chi organizza propone una lista di
possibili date/orari, i partecipanti indicano quando sono disponibili, e quando tutti
sono d'accordo su uno stesso slot il sistema crea automaticamente l'evento a calendario.

### 1.1 Utenti e ruoli

- **Organizzatore:** persona che crea la proposta di riunione. Deve autenticarsi. Le sue
  responsabilità: inserire i dati della riunione, definire gli slot orari candidati,
  specificare la lista dei partecipanti, impostare una scadenza per le risposte.
- **Partecipante:** persona invitata a esprimere la propria disponibilità. Non deve fare
  login. Le sue responsabilità: indicare su quali slot orari è disponibile, fornire i
  propri dati identificativi (nome, cognome, email).

Un utente può essere organizzatore di alcune proposte e partecipante di altre.

---

## 2. Flussi Principali

### 2.1 Organizzatore crea una proposta

1. L'organizzatore accede all'app (autenticato).
2. Compila un form con:
   - Titolo della riunione (obbligatorio)
   - Descrizione (opzionale)
   - Una lista di slot data/ora candidati (almeno 2)
   - Email dei partecipanti da invitare (almeno 1)
   - Una scadenza (deadline) entro cui i partecipanti devono rispondere
3. Il sistema crea la proposta, genera un link univoco per ogni partecipante,
   e invia un'email di invito a ciascuno con il proprio link.
4. L'organizzatore può vedere in una dashboard lo stato delle risposte in tempo reale.

### 2.2 Organizzatore monitora le risposte

1. L'organizzatore apre la dashboard.
2. Vede, per ogni proposta attiva, quali partecipanti hanno già risposto e quali no.
3. Per ogni slot orario, vede quanti partecipanti lo hanno approvato.
4. I dati si aggiornano man mano che i partecipanti rispondono.

### 2.3 Partecipante risponde all'invito

1. Il partecipante riceve un'email con un link personalizzato.
2. Clicca il link e arriva su una pagina dedicata alla proposta.
3. Vede il titolo, la descrizione, e la lista degli slot orari proposti.
4. Per ogni slot, può indicare se è disponibile (sì) o no.
5. Può selezionare "sì" su più slot contemporaneamente.
6. Prima di inviare la risposta, deve inserire nome, cognome ed email.
7. Inviati i voti, riceve una conferma a schermo.

### 2.4 Partecipante modifica le risposte

1. Il partecipante può riaprire il link ricevuto in qualsiasi momento.
2. Può cambiare i propri voti (aggiungere o togliere disponibilità sugli slot).
3. Le modifiche sono visibili in tempo reale all'organizzatore.
4. Può modificare fino a quando la proposta è aperta.

### 2.5 Consenso raggiunto e creazione evento

1. Quando ogni partecipante invitato ha indicato disponibilità sullo stesso slot orario,
   il consenso è raggiunto.
2. Immediatamente:
   - La proposta viene chiusa (nessun altro voto è accettato)
   - Il sistema crea un evento su Google Calendar dell'organizzatore con titolo,
     data/ora dello slot vincente, e lista dei partecipanti
   - Viene inviata un'email di notifica all'organizzatore e a tutti i partecipanti
     con i dettagli dell'evento creato
3. Se la creazione dell'evento su Google Calendar fallisce, il sistema riprova fino a
   3 volte. Se continua a fallire, invia comunque un'email all'organizzatore con tutti
   i dettagli dell'evento da creare manualmente.

### 2.6 Scadenza senza consenso (stallo)

1. Allo scadere della deadline, se nessuno slot ha ricevuto disponibilità da tutti i
   partecipanti, la proposta viene chiusa.
2. Il sistema invia un'email all'organizzatore con un riepilogo dei risultati parziali
   (per ogni slot: quanti sì ha ricevuto, su quanti partecipanti totali).
3. L'organizzatore può decidere se:
   - Annullare definitivamente la proposta
   - Riaprirla con nuovi slot e/o una nuova deadline

---

## 3. Criteri di Accettazione

### Creazione proposta
- [ ] L'organizzatore autenticato può creare una proposta con titolo, 2+ slot, 1+ email, deadline
- [ ] Il sistema valida i campi obbligatori e rifiuta proposte incomplete
- [ ] Il sistema genera un link univoco per ogni partecipante
- [ ] Il sistema invia un'email a ogni partecipante con il link
- [ ] La proposta appare nella dashboard dell'organizzatore

### Votazione
- [ ] Il partecipante clicca il link e vede tutti gli slot della proposta
- [ ] Il partecipante può selezionare "disponibile" su più slot
- [ ] Il partecipante deve inserire nome, cognome, email prima dell'invio
- [ ] Le risposte inviate appaiono nella dashboard organizzatore in tempo reale
- [ ] Il partecipante può riaprire il link e modificare le risposte (fino a chiusura)
- [ ] Un link usato da una persona non invitata mostra un messaggio di errore

### Consenso
- [ ] Quando l'ultimo partecipante indica disponibilità su uno slot già approvato da tutti
      gli altri, il consenso scatta immediatamente
- [ ] La proposta viene chiusa e non accetta più risposte
- [ ] Viene creato un evento su Google Calendar dell'organizzatore
- [ ] Viene inviata email di notifica a tutti
- [ ] Se Google Calendar fallisce dopo 3 tentativi, viene inviata email con dettagli
      per creazione manuale

### Stallo
- [ ] Alla scadenza, se nessuno slot ha l'accordo totale, la proposta si chiude
- [ ] L'organizzatore riceve email con riepilogo risultati parziali
- [ ] L'organizzatore può riaprire con nuovi slot e/o nuova deadline

### Edge case
- [ ] Partecipante che clicca il link dopo la chiusura vede un messaggio appropriato
- [ ] Organizzatore che aggiunge slot a proposta attiva: appaiono immediatamente
- [ ] Organizzatore che rimuove un partecipante: il calcolo del consenso si aggiorna
- [ ] Email duplicate nella lista partecipanti: vengono unificate
