---
theme: seriph
title: "AI per UI/UX — Sessione 1: Reiterazione dello Stile"
info: |
  Come usare l'AI per analizzare un'immagine di partenza
  e generare nuovi contenuti visivi coerenti.
class: text-center
drawings:
  persist: false
transition: slide-left
export:
  timeout: 60000
  wait: 3000
---

# AI per UI/UX

## Sessione 1 — Reiterazione dello Stile Visivo

<div class="abs-br m-6 text-sm opacity-50">
  Percorso in 3 sessioni — UI/UX Department
</div>

---
layout: default
---

# Perché l'AI nel Design?

<div class="grid grid-cols-2 gap-6 mt-8 text-sm">

<div>

### <twemoji-snail /> Senza AI

<div class="mt-4 space-y-2 text-xs opacity-70">

- Analizzi ogni immagine a occhio
- Estrai palette colore a mano
- Cerchi reference una per una
- Scrivi prompt solo dopo tentativi
- Ogni nuovo asset richiede ricominciare

</div>

</div>

<div v-click>

### <twemoji-high-voltage /> Con l'AI

<div class="mt-4 space-y-2">

<div class="p-2 bg-green-500/10 rounded-lg text-xs">

**Analisi istantanea** — carichi un'immagine e l'AI estrae stile, colori, proporzioni

</div>

<div class="p-2 bg-green-500/10 rounded-lg text-xs">

**Prompt automatico** — dall'analisi l'AI genera il prompt per nuovi asset coerenti

</div>

<div class="p-2 bg-green-500/10 rounded-lg text-xs">

**Variazioni infinite** — stesso stile, temi diversi, in pochi secondi

</div>

</div>

</div>

</div>

<div v-click class="mt-8 text-center text-sm opacity-70">
  Oggi partiamo dal workflow <b>più semplice</b> e <b>più immediato</b> da integrare.
</div>

---
layout: section
---

# Il Percorso in 3 Sessioni

<div class="mt-8 grid grid-cols-3 gap-4 text-sm max-w-4xl mx-auto">

<div class="p-4 bg-green-500/10 rounded-lg border-2 border-green-500/50">

### <twemoji-green-circle /> Oggi — Sessione 1

**Reiterazione dello Stile**

<div class="mt-2 text-xs opacity-70">
Il più semplice: analizza → prompt → genera
</div>

<div class="mt-3 text-xs">
<twemoji-stopwatch /> 30-40 minuti
</div>

</div>

<div class="p-4 bg-purple-500/10 rounded-lg border border-purple-500/30">

### <twemoji-yellow-circle /> Sessione 2

**Brand Identity**

<div class="mt-2 text-xs opacity-70">
Dall'ascolto del cliente alla brand guide
</div>

<div class="mt-3 text-xs">
<twemoji-stopwatch /> 60 minuti
</div>

</div>

<div class="p-4 bg-blue-500/10 rounded-lg border border-blue-500/30">

### <twemoji-blue-circle /> Sessione 3

**UI/UX Prototype**

<div class="mt-2 text-xs opacity-70">
Dalla discovery al prototipo animato su Figma
</div>

<div class="mt-3 text-xs">
<twemoji-stopwatch /> 90 minuti
</div>

</div>

</div>

<div class="mt-6 text-sm opacity-60 text-center">
  Ogni sessione aggiunge complessità. Si parte da ciò che l'AI fa meglio.
</div>

---
layout: default
---

# Il Workflow: 2 Fasi

<div class="mt-6 max-w-3xl mx-auto">

```mermaid {scale: 0.7}
graph LR
    A[Immagine<br/>di partenza] --> B[Fase 1<br/>Analisi AI]
    B --> C[Caratteristiche<br/>estratte]
    C --> D[Fase 2<br/>Prompt visivo]
    D --> E[Nuovi asset<br/>coerenti]
```

<div class="mt-8 grid grid-cols-2 gap-4 text-sm">

<div class="p-4 bg-blue-500/10 rounded-lg border border-blue-500/30">

### <twemoji-magnifying-glass-tilted-left /> Fase 1 — Analisi

L'AI estrae oggettivamente:
- Tipo di segno (linea / forma piena)
- Spessore del tratto
- Palette colori (HEX)
- Dettagli: angoli, curve, proporzioni
- Per foto: inquadratura, composizione, tono

</div>

<div class="p-4 bg-green-500/10 rounded-lg border border-green-500/30">

### <twemoji-writing-hand /> Fase 2 — Prompt

L'analisi diventa automaticamente un prompt:
- Descrizione sintetica dello stile
- Ottimizzato per Midjourney / DALL·E
- Riferimento all'immagine originale
- Pronto per generare variazioni

</div>

</div>

</div>

---
layout: default
---

# Fase 1 — Analisi dell'Immagine

<div class="grid grid-cols-2 gap-6 mt-6 text-sm">

<div>

### <twemoji-magnifying-glass-tilted-left /> Icone e Illustrazioni

<div class="mt-3 space-y-2">

<div class="p-3 bg-indigo-500/10 rounded-lg border border-indigo-500/30 text-xs">

<b>Prompt da usare:</b>

*"Analizza lo stile di questa icona/illustrazione: tipo di segno (linea o forma piena), spessore del tratto, colori utilizzati (HEX), proporzioni, livello di dettaglio, angoli e curve. Elenca le caratteristiche oggettive in una lista."*

</div>

<div v-click class="p-2 bg-gray-500/10 rounded-lg text-xs">

<b>Cosa ottieni:</b>
- <twemoji-check-mark-button /> Linea / forma piena
- <twemoji-check-mark-button /> Spessore tratto (px)
- <twemoji-check-mark-button /> Palette esatta (HEX)
- <twemoji-check-mark-button /> Raggio angoli, tipo curve
- <twemoji-check-mark-button /> Livello di dettaglio

</div>

</div>

</div>

<div v-click>

### <twemoji-camera-with-flash /> Immagini Fotografiche

<div class="mt-3 space-y-2">

<div class="p-3 bg-pink-500/10 rounded-lg border border-pink-500/30 text-xs">

<b>Prompt da usare:</b>

*"Analizza questa immagine: tipo di inquadratura, composizione, palette cromatica dominante (HEX), tono e atmosfera generale, coerenza tra soggetti."*

</div>

<div class="p-2 bg-gray-500/10 rounded-lg text-xs">

<b>Cosa ottieni:</b>
- <twemoji-check-mark-button /> Distanza / angolo
- <twemoji-check-mark-button /> Regola compositiva
- <twemoji-check-mark-button /> Palette dominante
- <twemoji-check-mark-button /> Mood / atmosfera
- <twemoji-check-mark-button /> Stile fotografico

</div>

</div>

</div>

</div>

---
layout: default
---

# Fase 2 — Dal Prompt alla Generazione

<div class="mt-4 text-sm">

<div class="max-w-3xl mx-auto space-y-3">

<div class="p-3 bg-green-500/10 rounded-lg border border-green-500/30">

### <twemoji-writing-hand /> Step 1: Converti l'analisi in prompt

Prendi l'output della Fase 1 e chiedi all'AI:

<div class="p-3 bg-gray-800/50 rounded-lg font-mono text-xs mt-2">
*"Converti questa analisi stilistica in un prompt ottimizzato per Midjourney, per generare nuove [icone / illustrazioni / immagini] coerenti con lo stesso stile."*
</div>

</div>

<div v-click class="p-3 bg-purple-500/10 rounded-lg border border-purple-500/30">

### <twemoji-artist-palette /> Step 2: Genera nuovi asset

Usa il prompt generato in Midjourney, DALL·E o Adobe Firefly:

<div class="p-3 bg-gray-800/50 rounded-lg font-mono text-xs mt-2">
*"Set of 6 [tema] icons in [stile], [spessore tratto], [palette], consistent stroke, SVG style, white background, grid layout"*
</div>

</div>

<div v-click class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

### <twemoji-counterclockwise-arrows-button /> Step 3: Itera e rifinisci

<div class="mt-2 text-xs space-y-1 opacity-70">
- Seleziona i risultati migliori
- Aggiusta manualmente su Figma se necessario
- Salva il prompt come template per progetti futuri
</div>

</div>

</div>

</div>

---
layout: default
---

# Tre Casi d'Uso

<div class="mt-6 grid grid-cols-3 gap-4 text-sm">

<div class="p-4 bg-indigo-500/10 rounded-lg border border-indigo-500/30">

### <twemoji-large-blue-diamond /> Icone

<div class="mt-3 text-xs space-y-2">

**Analisi:**
- Linea vs forma piena
- Spessore tratto
- Palette

**Prompt:**
*"12 outline icons, 2px stroke, #2E74B5, rounded corners 4px, minimal, for [theme]"*

<div class="mt-3 text-xs opacity-50">
Esempio: espandere un set di icone da 4 a 20
</div>

</div>

</div>

<div class="p-4 bg-pink-500/10 rounded-lg border border-pink-500/30">

### <twemoji-large-blue-diamond /> Illustrazioni

<div class="mt-3 text-xs space-y-2">

**Analisi:**
- Tratto / forma piena
- Palette colori
- Livello dettaglio

**Prompt:**
*"Illustration in flat style, [palette], [livello dettaglio], [tema], corporate but friendly, 4:3"*

<div class="mt-3 text-xs opacity-50">
Esempio: nuova sezione hero coerente con le illustrazioni esistenti
</div>

</div>

</div>

<div class="p-4 bg-teal-500/10 rounded-lg border border-teal-500/30">

### <twemoji-large-blue-diamond /> Immagini

<div class="mt-3 text-xs space-y-2">

**Analisi:**
- Inquadratura
- Composizione
- Mood

**Prompt:**
*"Professional photo, [inquadratura], [composizione], [mood], [soggetto], natural light, 16:9"*

<div class="mt-3 text-xs opacity-50">
Esempio: nuovi hero shot coerenti con lo stile fotografico del brand
</div>

</div>

</div>

</div>

---
layout: default
---

# Toolbox — Sessione 1

<div class="mt-6 grid grid-cols-2 gap-4 text-sm max-w-3xl mx-auto">

<div class="p-4 bg-gray-500/10 rounded-lg">

### <twemoji-speech-balloon /> Per l'analisi

<div class="mt-2 space-y-2 text-xs">

<div class="p-2 bg-green-500/10 rounded">

**ChatGPT (GPT-4o)**
Vision integrata — carichi l'immagine e analizza in un passaggio

</div>

<div class="p-2 bg-green-500/10 rounded">

**Claude**
Analisi testuale dettagliata, output strutturato

</div>

</div>

</div>

<div class="p-4 bg-gray-500/10 rounded-lg">

### <twemoji-artist-palette /> Per la generazione

<div class="mt-2 space-y-2 text-xs">

<div class="p-2 bg-purple-500/10 rounded">

**Midjourney**
Il migliore per coerenza stilistica, reference image

</div>

<div class="p-2 bg-purple-500/10 rounded">

**Adobe Firefly**
Integrato con Creative Cloud, perfetto per ritocchi

</div>

<div class="p-2 bg-purple-500/10 rounded">

**DALL·E 3**
Ottimo per iterazioni rapide, integrato in ChatGPT

</div>

</div>

</div>

</div>

---
layout: default
---

# Proviamolo — Esercizio Guidato

<div class="mt-6 max-w-3xl mx-auto text-sm space-y-4">

<div class="p-4 bg-blue-500/10 rounded-lg border border-blue-500/30">

### <twemoji-bullseye /> Obiettivo

Hai un set di 4 icone outline. Devi produrne altre 6 nello stesso stile.

</div>

<div v-click class="space-y-3">

<div class="p-3 bg-gray-500/10 rounded-lg">

<b>1. Carica l'icona in ChatGPT</b>
Usa il prompt di analisi:
*"Analizza lo stile di questa icona: tipo di segno, spessore tratto, colori, proporzioni, dettagli."*

</div>

<div v-click class="p-3 bg-gray-500/10 rounded-lg">

<b>2. Chiedi di convertire in prompt Midjourney</b>
*"Converti questa analisi in un prompt Midjourney per generare 6 nuove icone per i temi: impostazioni, utente, notifica, download, upload, calendario."*

</div>

<div v-click class="p-3 bg-gray-500/10 rounded-lg">

<b>3. Genera in Midjourney / DALL·E</b>
Prendi il prompt e genera. Seleziona i risultati migliori.

</div>

<div v-click class="p-3 bg-gray-500/10 rounded-lg">

<b>4. Aggiusta su Figma</b>
Importa le icone, verifica coerenza, aggiusta dettagli se necessario.

</div>

</div>

<div v-click class="p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30 text-center text-xs">

<b><twemoji-stopwatch /> Tempo stimato:</b> 15 minuti (contro 1-2 ore ridisegnando a mano)

</div>

</div>

---
layout: default
---

# Riepilogo — Sessione 1

<div class="mt-6 grid grid-cols-2 gap-4 text-sm max-w-3xl mx-auto">

<div class="p-4 bg-green-500/10 rounded-lg border border-green-500/30">

### <twemoji-check-mark-button /> Cosa hai imparato

<div class="mt-2 text-xs space-y-1">

- Caricare un'immagine e far analizzare lo stile all'AI
- Convertire l'analisi in un prompt generativo
- Generare nuovi asset visivi coerenti
- Iterare per affinare il risultato

</div>

</div>

<div class="p-4 bg-blue-500/10 rounded-lg border border-blue-500/30">

### <twemoji-key /> Key takeaway

<div class="mt-2 text-xs space-y-1">

- **L'analisi è il superpotere** — un buon prompt nasce da una buona analisi
- **Non serve reinventare** — l'AI replica stili esistenti in modo sorprendente
- **Tu decidi cosa tenere** — l'AI propone, il designer seleziona e rifinisce

</div>

</div>

</div>

<div class="mt-6 text-center text-sm opacity-70">
  Da oggi: ogni volta che devi produrre asset coerenti con uno stile esistente,<br/>
  <b>prima analizza con AI, poi genera.</b>
</div>

---
layout: center
class: text-center
---

# Prossima Sessione

## Brand Identity — Con l'AI

<div class="mt-8 text-lg opacity-70">
  Dall'ascolto del cliente alla brand guide.<br/>
  Benchmark automatizzati, concept generativi,<br/>
  documentazione accelerata.
</div>

<div class="mt-6 text-sm opacity-50">
  <twemoji-yellow-circle /> Sessione 2 di 3 — complessità intermedia
</div>
