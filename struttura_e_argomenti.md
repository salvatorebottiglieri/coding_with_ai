## **Modulo 1: Agentic Engineering \- Oltre l'uso passivo dell'AI**

In questa fase si passa dal vedere l'AI come un semplice "completatore di codice" a un vero e proprio collaboratore ingegneristico.

* **Teoria (20%):**  
  * Definizione di **Agentic Engineering**: la transizione dal semplice utilizzo dell'AI al lavoro simbiotico con essa.  
  * Differenza tra prompt engineering isolato e workflow agentici iterativi.  
* **Pratica (80%):**  
  * **Setup Ambiente:** Configurazione di un workspace dove l'agente ha accesso in lettura/scrittura al file system.  
  * **Laboratorio di Co-Progettazione:** Definizione di una specifica tecnica insieme all'agente. Invece di chiedere "scrivi questo", l'agente deve interrogare lo sviluppatore sui vincoli architetturali prima di procedere.

RIferimenti:

- [Agentic Engineering: Working With AI, Not Just Using It — Brendan O'Leary](https://youtu.be/BEKc4P87XKo?si=gOJg_sI0bBFUbm6X)

	

## **Modulo 2: Orchestrazione e Pattern Multi-Agente**

Il passaggio dal caos alla "coreografia" richiede di strutturare come più agenti collaborano su compiti complessi.

* **Teoria (20%):**  
  * Analisi dei pattern di orchestrazione multi-agente che funzionano realmente.  
  * Studio dei design pattern per agenti intelligenti tratti dal manuale *Agentic Design Patterns*.  
  * Confronto tra orchestrazione centralizzata e coreografia distribuita.  
* **Pratica (80%):**  
  * **Implementazione Pattern:** Costruire una pipeline in cui un "Agente Architetto" scompone un task e un "Agente Sviluppatore" implementa i singoli moduli.  
  * **Esercitazione di Refactoring:** Utilizzare un pattern multi-agente per analizzare una codebase legacy e proporre un piano di migrazione.

Riferimenti:

- [From Chaos to Choreography: Multi-Agent Orchestration Patterns That Actually Work — Sandipan Bhaumik](https://www.youtube.com/watch?v=2czYyrTzILg)  
- https://www.amazon.it/Agentic-Design-Patterns-Hands-Intelligent/dp/3032014018  
    
  


  ## **Modulo 3: Gestione del Contesto ad Alta Efficienza**

Imparare a fornire all'agente le informazioni giuste senza sprecare risorse o saturare i limiti del modello.

* **Teoria (20%):**  
  * Il concetto di **"Context That Costs Zero Tokens"**: come selezionare le informazioni rilevanti prima di inviarle all'LLM.  
* **Pratica (80%):**  
  * **Context Pruning Lab:** Sviluppare uno script che scansiona la codebase e genera un "riassunto del contesto" dinamico basato sul task corrente, minimizzando l'uso dei token.  
  * **RAG per Coding:** Integrare la documentazione locale del progetto come base di conoscenza per l'agente.

- [The Context That Costs Zero Tokens](https://www.youtube.com/watch?v=KTob5CZbx0k)

  ## **Modulo 4: Evals e Validazione Robusta**

L'accuratezza dichiarata dai modelli è spesso ingannevole; serve un sistema rigoroso per misurare la qualità reale.

* **Teoria (20%):**  
  * Perché l'accuratezza standard è "una bugia" e come approcciare la validazione robusta dei modelli.  
  * I **4 livelli di valutazione** che i team di sviluppo solitamente trascurano.  
  * Introduzione al framework **GEPA** (Generalized Evaluator Performance Assessment).  
* **Pratica (80%):**  
  * **Build a Judge:** Costruire un valutatore LLM ("Judge the Judge") utilizzando il framework GEPA per analizzare criticamente il codice prodotto.  
  * **Pipeline di Validazione:** Implementare un sistema di test automatizzato che non verifica solo se il codice "gira", ma se rispetta i criteri di qualità definiti nei 4 layer di valutazione.  
    

Riferimenti:

- [AI Agent Evals: The 4 Layers Most Teams Skip](https://www.youtube.com/watch?v=Kleu3ROhpvY&list=WL&index=1)  
- [Judge the Judge: Building LLM Evaluators That Actually Work with GEPA — Mahmoud Mabrouk, Agenta AI](https://www.youtube.com/watch?v=X4dEHRzBLmc&pp=ugUEEgJlbg%3D%3D)  
- [Your Accuracy Is a Lie — Here's How to Fix It (The Architect's Guide to Robust Model Validation)](https://www.youtube.com/watch?v=8eqCtf6iwDo&list=WL&index=3) (opzionale, non so ancora se inserirlo)

## PROJECT

Sviluppare un'applicazione di coordinamento che automatizza la creazione di eventi a calendario solo quando viene raggiunto il pieno consenso tra i partecipanti.   
Integrazione con google calendar per creare l’evento definitivo.

## CALENDARIO

### **Lezione 0: Fondamentali degli LLM e Anatomia degli Agenti**

**Obiettivo:** Comprendere l'architettura sottostante e la differenza tra un semplice modello linguistico e un sistema agentico autonomo.

| Tempo | Argomento | Dettaglio dei Contenuti | Fonte di Riferimento |
| :---- | :---- | :---- | :---- |
| **30 min** | **LLM Fundamentals** | Come "pensano" i modelli: tokenizzazione, finestre di contesto e la natura statistica del codice generato. Perché i fondamentali del software contano più che mai per validare questi output. |  |
| **30 min** | **Cos'è un Agente?** | Definizione di Agente rispetto a un semplice Chatbot. Il concetto di "Agentic Engineering": l'AI come entità che agisce, non solo risponde. | Brendan O'Leary / Eugene Yan |
| **30 min** | **L'Agent Harness** | Anatomia di un sistema agentico: il "guscio" (harness) che fornisce al modello strumenti, memoria e capacità di esecuzione. La differenza tra Harness e framework generici. | Agent Harness vs Everything |
| **30 min** | **Design Patterns & Loop** | Introduzione ai cicli di ragionamento (Reasoning Loops) e ai pattern di progettazione per rendere gli agenti intelligenti e affidabili. | Agentic Design Patterns (Libro) |

### **Lezione 1: Il Mindset dell'Agentic Engineering**

**Obiettivo:** Smettere di usare l'AI come un chatbot e iniziare a trattarla come un ingegnere operativo.

| Tempo | Attività | Dettaglio Argomenti | Fonte di Riferimento |
| :---- | :---- | :---- | :---- |
| **20 min** | **Teoria** | Differenza tra "usare" l'AI e "lavorare con" l'AI; i principi di Eugene Yan sulla collaborazione uomo-AI. | Brendan O'Leary / Eugene Yan |
| **30 min** | **Pratica 1** | Setup dell'ambiente: configurare i permessi di esecuzione e accesso ai file per l'agente. | Brendan O'Leary |
| **70 min** | **Pratica 2** | Esercizio di "Delega Attiva": scomposizione di un task complesso in micro-task per l'agente. | Brendan O'Leary / Eugene Yan |

### 

### 

### **Lezione 2: Architettura \- Harness vs Minimalismo**

**Obiettivo:** Comprendere come strutturare il "guscio" (harness) dell'agente e quando la semplicità vince sulla complessità.

| Tempo | Attività | Dettaglio Argomenti | Fonte di Riferimento |
| :---- | :---- | :---- | :---- |
| **20 min** | **Teoria** | Cos'è un Agent Harness; il contrasto tra l'approccio ingegneristico di OpenAI e il minimalismo di Mario Zechner. | Harness vs Everything / OpenAI / Mario Zechner |
| **40 min** | **Pratica 1** | Analisi di una "Harness Architecture" esistente: identificare i punti di controllo e validazione. | OpenAI Harness Engineering |
| **60 min** | **Pratica 2** | Lab: Costruire un agente minimale "pi" che risolve un problema specifico senza framework esterni. | Mario Zechner |

### 

### 

### 

### 

### 

### 

### 

### 

### 

### 

### 

### 

### 

### **Lezione 3: Fondamentali e il Problema dello "Slop"**

**Obiettivo:** Capire perché le basi dell'ingegneria del software sono più importanti ora che l'AI scrive il codice.

| Tempo | Attività | Dettaglio Argomenti | Fonte di Riferimento |
| :---- | :---- | :---- | :---- |
| **20 min** | **Teoria** | Perché i software fundamentals contano di più; definizione di "AI Slop" e come evitarlo. | Matt Pocock / Mario Zechner |
| **50 min** | **Pratica 1** | Code Review di codice generato: individuare pattern fragili o sovradimensionati prodotti dall'AI. | Matt Pocock |
| **50 min** | **Pratica 2** | Refactoring guidato: usare l'agente per ripulire lo "slop" applicando principi solidi di ingegneria. | Matt Pocock / Mario Zechner |

---

### 

### **Lezione 4: Workflow E2E e Implementazione Feature**

**Obiettivo:** Padroneggiare il flusso di lavoro completo dalla richiesta alla messa in produzione.

| Tempo | Attività | Dettaglio Argomenti | Fonte di Riferimento |
| :---- | :---- | :---- | :---- |
| **20 min** | **Teoria** | Walkthrough del workflow ideale per il coding assistito da AI: dalla pianificazione al commit. | Matt Pocock (Full Walkthrough) |
| **100 min** | **Pratica** | Workshop intensivo: Implementazione di una feature completa "End-to-End" utilizzando il workflow analizzato. | Matt Pocock (Full Walkthrough) |

