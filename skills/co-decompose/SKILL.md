---
name: co-decompose
description: Collaborative task decomposition where the agent interviews the human to co-build a live PRD plan file. Use when the user wants to plan a feature together, decompose a task with the agent, build a shared plan, or says "help me plan this" / "let's decompose this together" / "co-design this with me".
---

<what-to-do>

Interview me relentlessly about every aspect of this task until we reach a shared plan. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one.

Ask the questions one at a time, waiting for my answer before continuing.

For each question, provide your recommended answer when you have enough context to infer one.

</what-to-do>

<supporting-info>

## What this skill produces

A live **plan file** with 6 sections, updated incrementally as decisions crystallise during the interview:

1. **Goal** — what we are building and why
2. **Scope** — what's in and what's out
3. **Constraints** — technical, business, and time constraints
4. **User Stories** — who does what and why
5. **Acceptance Criteria** — how we know it's done
6. **Risks** — what could go wrong and mitigations

## Plan file format

Use the format defined in [PLAN-FORMAT.md](./PLAN-FORMAT.md). Create the file lazily — only when the first decision is made.

## During the session

### Walk the design tree branch by branch

Resolve dependencies in order. Start broad (goal, scope), then narrow (user stories, constraints), then validate (acceptance criteria, risks). Never jump to details before the foundation is clear.

### Ask one question at a time

Never batch multiple questions. Wait for the answer. Then write to the plan file. Then ask the next question.

### Provide a recommendation

For each question, when you have enough context, state your recommended answer and why. Let me agree, disagree, or refine.

### Sharpen fuzzy language

When I use vague or overloaded terms, propose precise alternatives. "You said 'notification' — do you mean email, push, in-app, or all three?"

### Discuss concrete scenarios

When user stories or acceptance criteria are being defined, stress-test them with specific scenarios. Invent edge cases that probe the boundaries.

### Challenge scope creep

When I add features that contradict the stated goal or constraints, flag it immediately. "That's a great idea, but it falls outside the scope you defined earlier. Do you want to expand scope?"

### Update the plan file live

After each resolved question, update the plan file immediately. Don't batch updates — capture them as they happen. The plan file should always reflect the current state of our understanding.

### Signal section completion

When a section is solid and the user confirms, mark it with a ✅ and move to the next one. The user always has the right to revisit earlier sections.

## When to stop

The interview is complete when all 6 sections have at least one entry and the user confirms the plan is ready. End with: "The plan is ready. Review it at [file path]. You can reopen any section at any time."

## Variants (deferred)

- **Designer variant** — task is a design system or UI component spec
- **HR variant** — task is an org process or policy rollout

These are deferred and should not be built yet.

</supporting-info>
