---
theme: seriph
title: "AI per UI/UX — Sessione 3: UI/UX Prototype"
info: |
  Come integrare l'AI in ogni fase del design di un prototipo UI/UX,
  dalla discovery al prototipo animato su Figma.
class: text-center
drawings:
  persist: false
transition: slide-left
---

# AI per UI/UX

## Sessione 3 — UI/UX Prototype

<div class="abs-br m-6 text-sm opacity-50">
  Percorso in 3 sessioni — UI/UX Department
</div>

---
layout: default
---

# Il Percorso Completo

<div class="mt-6 grid grid-cols-3 gap-4 text-sm">

<div class="p-4 bg-green-500/10 rounded-lg border border-green-500/30 opacity-60">

### ✅ Sessione 1

**Reiterazione Stile**

Analisi → prompt → generazione

</div>

<div class="p-4 bg-purple-500/10 rounded-lg border border-purple-500/30 opacity-60">

### ✅ Sessione 2

**Brand Identity**

Ascolto → benchmark → concept → consegna

</div>

<div class="p-4 bg-blue-500/10 rounded-lg border-2 border-blue-500/50">

### 🔵 Oggi — Sessione 3

**UI/UX Prototype**

Discovery → wireframe → visual → animazione

<div class="mt-2 text-xs opacity-70">
  Il workflow più complesso. Mettiamo insieme tutto.
</div>

</div>

</div>

<div class="mt-6 text-center text-sm opacity-70">
  Oggi applichiamo l'AI al flusso completo di progettazione di un'interfaccia.
</div>

---
layout: section
---

# UI/UX Prototype con l'AI

## 5 Fasi

<div class="mt-6 max-w-3xl mx-auto">

```mermaid {scale: 0.55}
graph LR
    A[🔍 Discovery<br/>& Analisi] --> B[📐 Wireframing]
    B --> C[🎨 Look & Feel]
    C --> D[🖌️ Visual Design<br/>su Figma]
    D --> E[🎬 Animazioni &<br/>Microinterazioni]
```

</div>

---
layout: default
---

# 1. Discovery e Analisi — Con l'AI

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div>

### 📋 Da caos a struttura

<div class="mt-2 text-xs opacity-70">
Note sparse, call, email → mappa navigazione e feature list.
</div>

<div class="mt-2 space-y-2">

<div class="p-3 bg-green-500/10 rounded-lg border border-green-500/30 text-xs">

<b>Competitor analysis istantanea</b>
*"Analizza le app [X, Y, Z]. Crea una tabella comparativa di: navigazione, pattern UX, onboarding, gestione errori, punti di forza e debolezze UI."*

</div>

<div v-click class="p-3 bg-green-500/10 rounded-lg border border-green-500/30 text-xs">

<b>Genera domande per interviste utente</b>
*"Genera 10 domande per un'intervista utente sul tema [X]. Target: [Y]. Obiettivo: capire bisogni e pain point attuali."*

</div>

<div v-click class="p-3 bg-green-500/10 rounded-lg border border-green-500/30 text-xs">

<b>Sintesi automatica da note grezze</b>
Dai in pasto trascrizioni di call, email, brief → AI produce:
- Mappa della navigazione
- Lista feature prioritizzate (must-have vs nice-to-have)
- Vincoli tecnici e di design

</div>

</div>

<div class="mt-2 text-xs opacity-60">
  ⏱️ Risparmio: 2-3 ore di sintesi → 15 minuti di revisione
</div>

</div>

<div v-click>

### 🗺️ Output strutturato

<div class="mt-2 space-y-2 text-xs">

<div class="p-2 bg-blue-500/10 rounded-lg">
<b>Prompt per la mappa:</b>
*"Per un'app di [tipo] con queste feature [elenco], quali sono le schermate principali e come si collegano? Qual è il flusso utente principale?"*
</div>

<div class="p-2 bg-blue-500/10 rounded-lg">
<b>Prompt per le priorità:</b>
*"Classifica queste feature [elenco] in must-have e nice-to-have per un MVP. Spiega perché per ciascuna."*
</div>

<div class="p-2 bg-blue-500/10 rounded-lg">
<b>Prompt per i vincoli:</b>
*"Basandoti sul framework [nome], quali vincoli di design devo considerare? Cosa posso e non posso fare?"*
</div>

</div>

</div>

</div>

---
layout: default
---

# 2. Wireframing — Con l'AI

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div>

### 📐 Da funzionalità a struttura

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

<b>Architettura delle schermate</b>
*"Per un'app di [tipo] con queste feature [elenco], quali schermate servono? Per ciascuna: azione principale, cosa vede l'utente per primo, cosa è secondario."*

</div>

<div v-click class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

<b>Suggerisci componenti per schermata</b>
*"Per la schermata [nome], che deve fare [azione], quali componenti UI sono più adatti? Considera che usiamo [framework]. Suggerisci layout e gerarchia."*

</div>

<div v-click class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

<b>Genera copy e microtesti</b>
*"Scrivi 5 varianti per il titolo e la CTA di una pagina che fa [X]. Tono: [brand voice]. Target: [utente]."*

</div>

</div>

</div>

<div v-click>

### 🤖 Tool specializzati

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

<b>Uizard</b> — Sketch / screenshot → wireframe
Carica uno schizzo o screenshot, genera wireframe interattivo editabile.

</div>

<div class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

<b>Galileo AI</b> — Testo → UI design
Descrivi la schermata in linguaggio naturale, genera il design completo.

</div>

<div class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

<b>Figma AI</b> — Plugin nativo
Genera layout, auto-layout, dummy content, varianti di componente.

</div>

</div>

<div class="mt-3 p-2 bg-yellow-500/10 rounded-lg text-xs text-center">
  <b>💡 Pro tip:</b> Usa l'AI per il <b>pensiero strutturale</b> (cosa va dove) e i tool per la <b>traduzione visiva</b> (come appare).
</div>

</div>

</div>

---
layout: default
---

# 3. Look & Feel — Con l'AI

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div>

### 🎨 Sistema visivo prima del design

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-pink-500/10 rounded-lg border border-pink-500/30">

<b>Generazione palette</b>
*"Genera una palette colori per un'app [settore] con tono [emozione]. Fornisci: primary, secondary, accent, success, warning, error, neutral scale (50-900). HEX per ciascuno."*

</div>

<div v-click class="p-3 bg-pink-500/10 rounded-lg border border-pink-500/30">

<b>Pairing tipografici</b>
*"Suggerisci 3 pairing tipografici per un'interfaccia [tipo]. Deve funzionare su [framework]. Includi: heading font, body font, scale (px), pesi."*

</div>

<div v-click class="p-3 bg-pink-500/10 rounded-lg border border-pink-500/30">

<b>Tono visivo</b>
*"Descrivi un mood visivo per [prodotto] che comunichi [valori]. Stile: [riferimenti]. Includi: trattamento immagini, iconografia, uso dello spazio."*

</div>

</div>

</div>

<div v-click>

### 🛠️ Strumenti dedicati

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-orange-500/10 rounded-lg border border-orange-500/30">

<b>Khroma</b> — AI color palette
Si allena sui colori che preferisci, genera combinazioni infinite con anteprima su UI.

</div>

<div class="p-3 bg-orange-500/10 rounded-lg border border-orange-500/30">

<b>Fontjoy</b> — AI font pairing
Deep learning per abbinamenti tipografici armonici con preview live.

</div>

<div class="p-3 bg-orange-500/10 rounded-lg border border-orange-500/30">

<b>Midjourney / DALL·E</b> — Moodboard
*"UI moodboard for [tipo] app, [stile], [colori], clean interfaces, 16:9, grid of 6"*

</div>

</div>

<div class="mt-3 p-2 bg-yellow-500/10 rounded-lg text-xs text-center">
  <b>💡 Pro tip:</b> Chiedi all'AI di adattare palette e tipografia al framework (Material, PrimeNG) per garantire implementabilità.
</div>

</div>

</div>

---
layout: default
---

# 4. Visual Design su Figma — Con l'AI

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div>

### 🖌️ Componenti e varianti

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-indigo-500/10 rounded-lg border border-indigo-500/30">

<b>Genera varianti di un componente</b>
*"Ho un pulsante primario con stile [colore, border-radius, padding]. Generami le specifiche per gli stati: default, hover, active, disabled, loading, error. Tema: [brand]."*

</div>

<div v-click class="p-3 bg-indigo-500/10 rounded-lg border border-indigo-500/30">

<b>Design system in miniatura</b>
*"Definisci un mini design system con token per: spacing (scale 4-32), border-radius (3 scale), shadow (3 livelli), font-scale (6 taglie). Adatto a [framework]. Output: tabella."*

</div>

<div v-click class="p-3 bg-indigo-500/10 rounded-lg border border-indigo-500/30">

<b>Dati realistici per mockup</b>
*"Genera 20 righe di dati fittizi in italiano per una tabella di [tipo]. Formato JSON. Includi: [campi]."*

</div>

</div>

</div>

<div v-click>

### 🔌 Plugin Figma + AI

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-teal-500/10 rounded-lg border border-teal-500/30">

<b>Figma AI</b>
- Auto-layout intelligente
- Riempimento automatico con dati
- Suggerimenti in linea col design system

</div>

<div class="p-3 bg-teal-500/10 rounded-lg border border-teal-500/30">

<b>Magician</b>
- Testo → icone SVG direttamente in Figma
- Riscrittura copy nei frame
- Generazione immagini da prompt

</div>

<div class="p-3 bg-teal-500/10 rounded-lg border border-teal-500/30">

<b>Similayer</b>
- Seleziona elementi simili in un click
- Rinomina e organizza layer automaticamente

</div>

</div>

<div class="mt-3 text-xs opacity-60 text-center">
  ⚠️ L'AI accelera la costruzione. La coerenza visiva e l'usabilità restano tue.
</div>

</div>

</div>

---
layout: default
---

# 5. Animazioni e Microinterazioni — Con l'AI

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div>

### 🎬 Specifiche di animazione

<div class="mt-2 text-xs opacity-70">
L'animazione serve a rendere esplicito il cambio di stato.
</div>

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

<b>Genera specifiche</b>
*"Per un dropdown che si apre, suggerisci durata, easing curve e comportamento dell'animazione. Output: durata, CSS easing, descrizione del comportamento."*

</div>

<div v-click class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

<b>Microinterazioni complete</b>
*"Quali microinterazioni servono in una tabella che supporta: filtro, ordinamento, espansione riga, selezione multipla? Per ciascuna: trigger, animazione, feedback visivo."*

</div>

<div v-click class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

<b>Genera codice CSS / Lottie</b>
*"Scrivi il CSS per un'animazione di skeleton loading. 3 varianti: card (370x200), riga tabella (full width x 48), avatar (40x40 circle)."*

</div>

</div>

</div>

<div v-click>

### 🛠️ Strumenti

<div class="mt-2 space-y-2 text-xs">

<div class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

<b>Jitter</b> — Animazioni UI senza codice
Importa da Figma, anima con timeline visuale. Export video/GIF/Lottie.

</div>

<div class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

<b>Rive</b> — Animazioni interattive
State machine visuali per microinterazioni complesse. Export per web e mobile.

</div>

<div class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

<b>LottieFiles</b> — Player + editor
Libreria di animazioni pronte + AI per generare nuove. Integrazione con Figma.

</div>

</div>

</div>

</div>

---
layout: default
---

# Riepilogo Finale — Dove l'AI ti Accelera

<div class="mt-4 grid grid-cols-2 gap-4 text-sm">

<div class="p-4 bg-green-500/10 rounded-lg border border-green-500/30">

### ⚡ L'AI è già forte in

<div class="mt-2 space-y-1 text-xs">

- ✅ **Analisi competitor e benchmark** — da ore a minuti
- ✅ **Generazione testi**: copy, CTA, microcopy, razionali, documentazione
- ✅ **Generazione asset**: moodboard, icone, illustrazioni, varianti
- ✅ **Esplorazione palette e tipografia** — combinazioni illimitate
- ✅ **Specifiche tecniche**: CSS, easing, token, scale
- ✅ **Sintesi**: da note sparse a documenti strutturati
- ✅ **Reiterazione stile**: da 1 immagine a N asset coerenti

</div>

</div>

<div class="p-4 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

### 🧠 Serve il tuo giudizio per

<div class="mt-2 space-y-1 text-xs">

- 🧠 **Scelte strategiche** — l'AI non conosce il cliente
- 🧠 **Coerenza complessiva** — gusto e occhio restano tuoi
- 🧠 **Fattibilità tecnica** — l'AI ignora i vincoli reali del framework
- 🧠 **Relazione col cliente** — empatia, ascolto, fiducia
- 🧠 **Approvazione finale** — l'AI propone, tu decidi

</div>

</div>

</div>

<div class="mt-4 p-4 bg-blue-500/10 rounded-lg border border-blue-500/30 text-center">

<div class="text-lg font-bold">La regola d'oro</div>
<div class="mt-1 text-sm">
  L'AI ti fa risparmiare il <b>60-70% del tempo operativo</b><br/>
  (ricerca, bozze, varianti, documentazione).<br/>
  Tu investi il tempo guadagnato nella <b>qualità strategica e creativa</b>.
</div>

</div>

---
layout: default
---

# Piano di Adozione — Da Dove Iniziare

<div class="mt-6 grid grid-cols-3 gap-4 text-sm max-w-4xl mx-auto">

<div class="p-4 bg-blue-500/10 rounded-lg border border-blue-500/30">

### 🟢 Subito — Questa settimana

<div class="mt-2 text-xs space-y-1">

- **ChatGPT/Claude** per analisi competitor e benchmark
- Prompt per generare domande intervista
- Sintesi automatica note meeting → brief
- Analisi stile da immagine (Sessione 1)

</div>

<div class="mt-3 text-xs opacity-50">
  ⏱️ Impatto immediato, curva di apprendimento minima
</div>

</div>

<div class="p-4 bg-purple-500/10 rounded-lg border border-purple-500/30">

### 🟡 Prossimo mese

<div class="mt-2 text-xs space-y-1">

- **Midjourney/DALL·E** per moodboard e asset exploration
- **Figma AI** e **Magician** nel workflow quotidiano
- **Khroma / Fontjoy** per palette e tipografia
- Brand identity assistita (Sessione 2)

</div>

<div class="mt-3 text-xs opacity-50">
  Richiede un po' di pratica con i prompt generativi
</div>

</div>

<div class="p-4 bg-green-500/10 rounded-lg border border-green-500/30">

### 🔵 Entro 2-3 mesi

<div class="mt-2 text-xs space-y-1">

- **Uizard / Galileo AI** per wireframe rapidi
- **Jitter / Rive** per animazioni e prototipi
- **Reiterazione stile** sistematica nell'asset pipeline
- UI/UX prototype end-to-end (Sessione 3)

</div>

<div class="mt-3 text-xs opacity-50">
  Workflow completamente integrato
</div>

</div>

</div>

<div class="mt-6 text-center text-sm">
  <b>Non serve rivoluzionare tutto subito.</b> Un tool alla volta, un workflow alla volta.
</div>

---
layout: default
---

# Toolbox Completo

<div class="mt-4 grid grid-cols-3 gap-3 text-sm">

<div class="p-3 bg-gray-500/10 rounded-lg">

### 💬 Chat / Analisi

- **ChatGPT (GPT-4o)** — vision, analisi, testo
- **Claude** — analisi documenti, sintesi
- **Perplexity** — ricerca con fonti

</div>

<div class="p-3 bg-gray-500/10 rounded-lg">

### 🎨 Generazione Immagini

- **Midjourney** — coerenza stilistica
- **DALL·E 3** — iterazioni rapide
- **Adobe Firefly** — integrato CC

</div>

<div class="p-3 bg-gray-500/10 rounded-lg">

### 🖌️ Design & UI

- **Figma AI** — plugin nativi
- **Magician** — icone, copy, immagini
- **Uizard** — sketch → wireframe
- **Galileo AI** — testo → UI

</div>

<div class="p-3 bg-gray-500/10 rounded-lg">

### 🎬 Animazione

- **Jitter** — animazioni no-code
- **Rive** — state machine
- **LottieFiles** — libreria + AI

</div>

<div class="p-3 bg-gray-500/10 rounded-lg">

### 🌈 Colori & Font

- **Khroma** — palette AI
- **Fontjoy** — font pairing
- **Coolors** — palette generation

</div>

<div class="p-3 bg-gray-500/10 rounded-lg">

### 📄 Documentazione

- **ChatGPT / Claude** — testi
- **Gamma** — presentazioni AI
- **Notion AI** — documentazione

</div>

</div>

---
layout: center
class: text-center
---

# Fine del Percorso 🎉

<div class="mt-8 text-xl opacity-80">
  Hai gli strumenti per integrare l'AI<br/>
  in ogni fase del tuo workflow creativo.
</div>

<div class="mt-8 grid grid-cols-3 gap-6 max-w-3xl mx-auto text-sm">

<div class="p-3 bg-green-500/10 rounded-lg">
  <b>Sessione 1</b><br/>
  <span class="opacity-70">Reiterazione stile</span>
</div>

<div class="p-3 bg-purple-500/10 rounded-lg">
  <b>Sessione 2</b><br/>
  <span class="opacity-70">Brand Identity</span>
</div>

<div class="p-3 bg-blue-500/10 rounded-lg">
  <b>Sessione 3</b><br/>
  <span class="opacity-70">UI/UX Prototype</span>
</div>

</div>

<div class="mt-10 text-lg opacity-50">
  <em>"L'AI non ti sostituisce.<br/>Ti restituisce il tempo per fare la differenza."</em>
</div>

---
layout: center
class: text-center
---

<div class="mb-8">
  <div class="text-7xl font-bold bg-gradient-to-r from-purple-400 via-pink-400 to-orange-400 bg-clip-text text-transparent">
    Domande?
  </div>
</div>

<div class="mt-8 text-lg opacity-70">
  Feedback, dubbi, casi d'uso specifici?
</div>

<div class="mt-6 text-sm opacity-50">
  Francesca — UI/UX Department
</div>
