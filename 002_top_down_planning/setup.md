---
theme: seriph
title: Lesson 2 — Pre-Lesson Setup
info: |
  ## Pre-lesson Setup — Top-Down Planning
  Complete these steps before attending Lesson 2
class: text-center
drawings:
  persist: false
transition: slide-left
---

# Pre-Lesson Setup

## Top-Down Planning — Lesson 2

<div class="abs-br m-6 flex gap-2">
  <span class="text-sm opacity-50">Complete before the lesson</span>
</div>

<div v-click class="mt-8 p-4 bg-yellow-500/10 rounded-lg border border-yellow-500/30 text-sm max-w-lg mx-auto">
  <span class="opacity-70">Your plan.md from Lesson 1 + Matt Pocock's skills installed.</span>
</div>

---
layout: default
---

# 1. Bring Your plan.md

<div class="grid grid-cols-2 gap-6 mt-8">

<div>

### What you need

<div class="text-sm mt-4 space-y-3">

<div class="p-3 bg-blue-500/10 rounded-lg">

**Your group's plan.md** from Lesson 1 — with the 6 sections filled in:
- Goal
- Scope
- Constraints
- User Stories
- Acceptance Criteria
- Risks

</div>

<div v-click class="p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

This document is the **starting material** for the grilling session that produces your PRD.

</div>

</div>

</div>

<div v-click>

### If you missed Lesson 1

<div class="text-sm mt-4 space-y-3">

<div class="p-3 bg-gray-500/10 rounded-lg">

Join an existing group. You can still contribute — fresh eyes catch things the group might have missed.

</div>

<div class="p-3 bg-green-500/10 rounded-lg">

Read the Lesson 1 slides to understand the Delegation Workflow principles, especially **"Plan Then Act"**.

</div>

</div>

</div>

</div>

---

# 2. Install Matt Pocock's Skills

<div class="grid grid-cols-2 gap-4 mt-6 text-sm">

<div>

### What these skills do

<div class="mt-3 p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

Matt Pocock's skills are **process guides** — they teach the agent *how* to work with you, not just what documents to load. The key ones you'll use:

- **`/grill-with-docs`** — interviews you relentlessly, one question at a time, building a shared language and ADRs as you go
- **`/to-prd`** — synthesizes everything from the conversation into a structured PRD
- **`/domain-modeling`** — actively sharpens domain terms and writes CONTEXT.md + ADRs
- **`/tdd`** — guides the red-green-refactor test loop (Lesson 3)

</div>

</div>

<div v-click>

### Installation (30 seconds)

<div class="mt-3 space-y-2">

<div class="p-2 bg-gray-500/10 rounded">

**1.** Run the installer in your terminal:

```bash
npx skills@latest add mattpocock/skills
```

</div>

<div class="p-2 bg-gray-500/10 rounded">

**2.** Pick the skills you want and which coding agents to install them on. **Make sure you select `/setup-matt-pocock-skills`.**

</div>

<div class="p-2 bg-gray-500/10 rounded">

**3.** In Copilot Chat, run `/setup-matt-pocock-skills`. It will ask:
- Which issue tracker to use (GitHub, Linear, or local files)
- What labels you apply to tickets
- Where to save docs

</div>

<div class="p-2 bg-gray-500/10 rounded">

**4.** Verify: in Copilot, type `/grill-with-docs` and confirm the skill is recognized.

</div>

</div>

</div>

</div>

<div v-click class="mt-4 p-2 bg-green-500/10 rounded-lg border border-green-500/30 text-xs text-center">

<b>These are the real skills</b> from <a href="https://github.com/mattpocock/skills">github.com/mattpocock/skills</a> — used daily by experienced engineers. They're small, composable, and work with any model.

</div>

---
layout: default
---

# 3. Understand the Philosophy

<div class="mt-6 text-sm">

### This is one approach — not the only one

<div class="mt-4 space-y-3">

<div class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

### Matt Pocock's core ideas

<div class="mt-2 space-y-1">

- **Skills are process guides, not document loaders.** They orchestrate how the agent works — not which files to read.
- **Documents are lightweight.** An ADR is 1-3 sentences. CONTEXT.md is a glossary, not a design doc.
- **Documents are outputs of the process.** You grill → terms crystallize → write them down. Not: write 50 documents → start coding.
- **Only record what's worth recording.** ADRs only for surprising, hard-to-reverse, trade-off decisions. Most things don't need them.
- **The agent helps, you decide.** The agent structures your thinking — it doesn't replace your judgment.

</div>

</div>

<div v-click class="p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

### Other philosophies you should know about

- **BDD (Cucumber/Gherkin)** — executable specs in human-readable Given/When/Then format. More process, but the spec *is* the test.
- **Design Systems** — dedicated component libraries with visual rules. Great for UI-heavy projects with multiple contributors.
- **50+ ADR approaches** — comprehensive architecture documentation with lint-enforced rules. More documentation, stronger guarantees.
- **Spec-Kit / BMAD** — full workflow ownership by the tool. Less control, more automation.

<div class="mt-2 text-xs opacity-60">
  We're using Matt's approach today because it's lightweight, composable, and gives you the most control.<br/>
  No approach is universally "correct." Pick what works for your team and your context.
</div>

</div>

<div v-click class="p-3 bg-green-500/10 rounded-lg border border-green-500/30">

<b>💡 Mental model:</b> Think of CONTEXT.md, ADRs, and PRDs as your project's **external memory** — for both humans and AI agents. Without them, decisions are lost when people leave and context compacts. But keep them lightweight — the goal is clarity, not bureaucracy.

</div>

</div>

</div>

---
layout: default
---

# 4. Folder Structure — Prepare Your Workspace

<div class="mt-6">

### Create this structure in your group's workspace

<div class="text-sm mt-4">

```
your-group-workspace/
├── plan.md                  ← from Lesson 1
├── docs/
│   ├── CONTEXT.md           ← you'll build this (domain glossary)
│   └── adr/
│       ├── 0001-slug.md      ← you'll write this
│       └── 0002-slug.md      ← you'll write this
└── prd/
    └── calendar-app.md       ← you'll write this
```

</div>

<div v-click class="mt-4 p-3 bg-blue-500/10 rounded-lg border border-blue-500/30 text-xs">

<b>💡 Tip:</b> Create the folders before the lesson. CONTEXT.md and ADRs go under `docs/` (the standard location in Matt's workflow). The PRD goes in its own directory. This saves time and lets you jump straight into building content.

</div>

</div>

---
layout: center
class: text-center
---

# Ready for the Lesson

<div class="mt-8 text-lg opacity-80">
  Before attending, make sure:
</div>

<div class="mt-8 max-w-md mx-auto text-left space-y-4 text-sm">

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>plan.md</b> from Lesson 1 available</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>Matt Pocock's skills</b> installed in VS Code/Copilot via <code>npx skills@latest</code></div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>/setup-matt-pocock-skills</b> run in your project repo</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>Folder structure</b> created (docs/adr/, prd/)</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>Philosophy understood:</b> skills are process guides, documents are lightweight, ADRs are for surprising decisions only</div>
</div>

</div>

<div v-click class="mt-8 p-4 bg-green-500/10 rounded-lg border border-green-500/30 text-sm">
  <b>You're all set.</b> See you at the lesson!
</div>
