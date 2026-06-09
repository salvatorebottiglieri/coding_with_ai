---
theme: seriph
title: Lesson 1 — Environment Setup
info: |
  ## Pre-lesson Setup — Agentic Engineering Module
  Complete these steps before attending Lesson 1
class: text-center
drawings:
  persist: false
transition: slide-left
---

# Pre-Lesson Setup

## Agentic Engineering — Lesson 1

<div class="abs-br m-6 flex gap-2">
  <span class="text-sm opacity-50">Complete before the lesson</span>
</div>

<div v-click class="mt-8 p-4 bg-yellow-500/10 rounded-lg border border-yellow-500/30 text-sm max-w-lg mx-auto">
  <span class="opacity-70">VS Code + Copilot and the co-decompose skill.</span>
</div>

---
layout: default
---

# 1. VS Code + GitHub Copilot

<div class="grid grid-cols-2 gap-6 mt-8">

<div>

### Installation

<div class="text-sm mt-4 space-y-4">

<div class="p-3 bg-gray-500/10 rounded-lg">

**1. VS Code** — https://code.visualstudio.com/
Download and install the latest stable version

</div>

<div v-click class="p-3 bg-gray-500/10 rounded-lg">

**2. GitHub Copilot extension**
Open VS Code → Extensions (Ctrl+Shift+X) → search "GitHub Copilot" → Install

</div>

<div v-click class="p-3 bg-gray-500/10 rounded-lg">

**3. Authentication**
Click the Copilot icon in the bottom right → Sign in with GitHub

</div>

</div>

</div>

<div v-click>

### Verification

<div class="text-sm mt-4 space-y-3">

<div class="p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

Open the Chat panel (Ctrl+Shift+I) and type:

```
Hello, who are you and what can you do?
```

</div>

<div class="p-3 bg-green-500/10 rounded-lg border border-green-500/30">

If Copilot responds, installation is complete.

</div>

<div class="p-3 bg-red-500/10 rounded-lg border border-red-500/30 text-xs">

If it doesn't respond: verify GitHub authentication and internet connection.

</div>

</div>

</div>

</div>

---

# 2. Loading the `co-decompose` Skill

<div class="mt-6 grid grid-cols-2 gap-4 text-sm">

<div>

### What is a skill

<div class="mt-3 p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

A specialized instruction module the agent loads when it detects a certain task. Extends capabilities without rewriting everything.

</div>

</div>

<div v-click>

### Load the skill

<div class="mt-3 space-y-2">

<div class="p-2 bg-gray-500/10 rounded">

**1.** Download `co-decompose.zip` from the course repo

</div>

<div class="p-2 bg-gray-500/10 rounded">

**2.** Extract to `~/.agents/skills/co-decompose/` (create the `.agents/skills` folders inside your home directory if they don't already exist)

</div>

<div class="p-2 bg-gray-500/10 rounded">

**3.** Ask Copilot: *"Do you see the co-decompose skill?"*

</div>

</div>

</div>

</div>

<div v-click class="mt-4 p-2 bg-green-500/10 rounded-lg border border-green-500/30 text-xs text-center">

<b>Copilot loads the skill automatically</b> when you start a planning conversation.

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
  <div><b>VS Code + Copilot</b> installed and authenticated</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[x]</span>
  <div><b>co-decompose skill</b> loaded in your workspace</div>
</div>

</div>

<div v-click class="mt-8 p-4 bg-green-500/10 rounded-lg border border-green-500/30 text-sm">
  <b>You're all set.</b> See you at the lesson!
</div>
