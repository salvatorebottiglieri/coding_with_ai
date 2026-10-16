---
theme: seriph
title: Lesson 3 — Pre-Lesson Setup
info: |
  ## Pre-lesson Setup — The Complete Loop
  Complete these steps before attending Lesson 3
class: text-center
drawings:
  persist: false
transition: slide-left
---

# Pre-Lesson Setup

## The Complete Loop — Lesson 3

<div class="abs-br m-6 flex gap-2">
  <span class="text-sm opacity-50">Complete before the lesson</span>
</div>

<div v-click class="mt-8 p-4 bg-yellow-500/10 rounded-lg border border-yellow-500/30 text-sm max-w-lg mx-auto">
  <span class="opacity-70">Your CONTEXT.md, ADRs, PRD, and issues from Lesson 2 — in a working repo where you can run tests.</span>
</div>

---
layout: default
---

# 1. Bring Your Lesson 2 Artifacts

<div class="grid grid-cols-2 gap-6 mt-8">

<div>

### What you need

<div class="text-sm mt-4 space-y-3">

<div class="p-3 bg-blue-500/10 rounded-lg">

**CONTEXT.md** — the domain glossary. The agent will read this before writing any code. If it's incomplete, names will drift.

</div>

<div class="p-3 bg-blue-500/10 rounded-lg">

**ADRs** — architecture decisions. The agent must respect them during implementation. Know which ADRs are relevant to the ticket you'll pick.

</div>

<div class="p-3 bg-green-500/10 rounded-lg border border-green-500/30">

**Issues** — the vertical slice list. You'll pick one to implement. Each issue should have a clear acceptance criterion.

</div>

<div v-click class="p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

Read through your issues before the lesson and **pre-select a candidate** — one that is small, independent, and has a clear done criterion.

</div>

</div>

</div>

<div v-click>

### If you missed Lesson 2

<div class="text-sm mt-4 space-y-3">

<div class="p-3 bg-gray-500/10 rounded-lg">

Use the teacher example from `002_top_down_planning/teacher_example/` — it has a complete CONTEXT.md, ADRs, and issues you can implement against.

</div>

<div class="p-3 bg-green-500/10 rounded-lg">

Pick Issue 01 from the teacher example: "Organizer OAuth flow and proposal creation." It's self-contained and testable.

</div>

</div>

</div>

</div>

---
layout: default
---

# 2. Set Up a Working Repo

<div class="grid grid-cols-2 gap-4 mt-6 text-sm">

<div>

### What "working" means

<div class="mt-3 p-3 bg-blue-500/10 rounded-lg border border-blue-500/30">

You need a repo where you can:

- **Run tests** — any test runner works (`npm test`, `pytest`, etc.)
- **See test failures** — the agent reads the failure output
- **Commit code** — you'll open a PR at the end

The project doesn't need to be a full app. A minimal scaffold with a working test runner is enough.

</div>

<div v-click class="mt-3 p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30">

### If you don't have a repo yet

Ask the agent to scaffold one:

```
"Create a minimal Node.js project for the Calendar
Consensus App with TypeScript and Vitest.
No framework. Just a working test runner."
```

</div>

</div>

<div v-click>

### Folder structure to have ready

<div class="mt-3 text-sm">

```
your-project/
├── docs/
│   ├── CONTEXT.md         ← from Lesson 2
│   └── adr/
│       └── 0001-slug.md   ← your ADRs
├── issues/
│   └── 01-your-ticket.md  ← the ticket you'll implement
├── src/                   ← empty (agent fills this)
├── tests/                 ← empty (agent fills this)
└── package.json           ← test runner configured
```

</div>

<div v-click class="mt-3 p-2 bg-green-500/10 rounded-lg text-xs">
<b>💡 Tip:</b> The <code>src/</code> and <code>tests/</code> folders should be empty. The agent builds them from scratch — that's the point.
</div>

</div>

</div>

---
layout: default
---

# 3. Understand the READY / RE_WORK Fork

<div class="mt-4 text-sm text-center opacity-70">
  Today you'll be the one making this call. Internalize the two checks.
</div>

<div class="mt-6 grid grid-cols-2 gap-4">

<div class="p-4 bg-blue-500/10 rounded-lg border border-blue-500/30">

### 🤖 Auto-check (objective, agent runs it)

<div class="text-sm mt-2 space-y-1">

- All tests pass
- No regressions in existing tests
- Types compile without errors

<div class="mt-2 text-xs p-2 bg-gray-500/10 rounded">
<b>Result:</b> agent says "propose READY." You still review.
</div>

</div>

</div>

<div class="p-4 bg-purple-500/10 rounded-lg border border-purple-500/30">

### 👁️ Functional review (judgment, you do it)

<div class="text-sm mt-2 space-y-1">

- Does it match the user story?
- Is the behavior correct end-to-end?
- Are names aligned with CONTEXT.md?
- Are ADRs respected?
- Is scope contained?

<div class="mt-2 text-xs p-2 bg-gray-500/10 rounded">
<b>Result:</b> READY → open PR. RE_WORK → give targeted feedback.
</div>

</div>

</div>

</div>

<div v-click class="mt-4 p-3 bg-yellow-500/10 rounded-lg border border-yellow-500/30 text-xs text-center">
  <b>Key mental shift:</b> "the tests pass" ≠ "it's READY." Tests prove the code runs — not that it does the right thing.<br/>
  The functional review is what closes the gap.
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
  <div><b>CONTEXT.md</b> from Lesson 2 available (or teacher example)</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>ADRs and issues</b> from Lesson 2 available</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>Working repo</b> — test runner configured, <code>npm test</code> runs without errors</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>Candidate ticket pre-selected</b> — small, independent, clear acceptance criterion</div>
</div>

<div class="p-3 bg-gray-500/10 rounded-lg flex items-start gap-3">
  <span class="text-lg">[ ]</span>
  <div><b>READY/RE_WORK understood:</b> auto-check (tests) + functional review (user story match)</div>
</div>

</div>

<div v-click class="mt-8 p-4 bg-green-500/10 rounded-lg border border-green-500/30 text-sm">
  <b>You're all set.</b> See you at the lesson!
</div>
