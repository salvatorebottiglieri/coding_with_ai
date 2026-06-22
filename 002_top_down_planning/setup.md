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
  <span class="opacity-70">Your plan.md from Lesson 1 + the <code>decision-stack</code> skill.</span>
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

This document is the **starting material** for your PRD.

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

# 2. Install the `decision-stack` Skill

<div class="grid grid-cols-2 gap-4 mt-6 text-sm">

<div>

### The skill

<div class="mt-3 p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

The `decision-stack` skill teaches the agent how to help you write ADRs, PRDs, and BDD scenarios. The agent uses it to:
- Ask targeted questions (one at a time)
- Structure documents correctly
- Connect documents with cross-references
- Check for completeness

</div>

</div>

<div v-click>

### Installation

<div class="mt-3 space-y-2">

<div class="p-2 bg-gray-500/10 rounded">

**1.** Download `decision-stack.zip` from the course repo

</div>

<div class="p-2 bg-gray-500/10 rounded">

**2.** Extract to `~/.agents/skills/decision-stack/`

</div>

<div class="p-2 bg-gray-500/10 rounded">

**3.** Verify in Copilot: *"Do you see the decision-stack skill?"*

</div>

<div class="p-2 bg-gray-500/10 rounded">

**4.** Test it: *"Help me draft an ADR for a simple decision, ask me one question at a time"*

</div>

</div>

</div>

</div>

<div v-click class="mt-4 p-2 bg-green-500/10 rounded-lg border border-green-500/30 text-xs text-center">

<b>Copilot loads the skill automatically</b> when you start a planning conversation about ADRs, PRDs, or BDD.

</div>

---
layout: default
---

# 3. Pre-Read: The Decision Stack Concept

<div class="mt-6 text-sm">

### Watch or read (optional but recommended)

<div class="mt-4 space-y-3">

<div class="p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

**🎥 Video (10 min):** *"Capturing Decisions for Humans and AI Alike"* — Michal
<div class="text-xs mt-1 opacity-60">https://www.youtube.com/watch?v=504PvfXou5Y</div>

</div>

<div v-click class="p-3 bg-green-500/10 rounded-lg border border-green-500/30">

### Key ideas to remember

<div class="mt-2 space-y-1">

- Humans and LLMs have the **same problem**: limited context, they forget
- **ADR** = why you build it this way, and how you enforce it
- **PRD** = what problem it solves, and the user journey
- **BDD** = executable specifications in human language
- **Design System** = consistent UI from documented components
- **The Loop** = git hooks → CI → agent reads → agent fixes

</div>

</div>

<div v-click class="p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

<b>💡 Mental model:</b> These documents are not bureaucracy — they're the **external memory** for both humans and AI agents. Without them, decisions are lost when people leave and context compacts.

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
├── plan.md              ← from Lesson 1
├── adr/
│   ├── 001-auth.md       ← you'll write this
│   ├── 002-data.md       ← you'll write this
│   └── 003-api.md        ← you'll write this
├── prd/
│   └── calendar-app.md   ← you'll write this
└── bdd/
    ├── voting.feature     ← you'll write this
    └── edge-cases.feature ← you'll write this
```

</div>

<div v-click class="mt-4 p-3 bg-blue-500/10 rounded-lg border border-blue-500/30 text-xs">

<b>💡 Tip:</b> Create the folders and empty files before the lesson. This saves time and lets you jump straight into writing content.

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
  <span class="text-lg">[x]</span>
  <div><b>plan.md</b> from Lesson 1 available</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[x]</span>
  <div><b>decision-stack skill</b> installed in VS Code/Copilot</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[x]</span>
  <div><b>Folder structure</b> created (adr/, prd/, bdd/)</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[x]</span>
  <div><b>Video watched</b> (or at least skimmed the transcript)</div>
</div>

</div>

<div v-click class="mt-8 p-4 bg-green-500/10 rounded-lg border border-green-500/30 text-sm">
  <b>You're all set.</b> See you at the lesson!
</div>
