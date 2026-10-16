# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

## Configured layout

This repository is configured as **single-context**.

## Before exploring, read these

- **`CONTEXT.md`** at the repo root
- **`docs/adr/`** for architecture decisions that touch the area being changed

If any of these files don't exist, proceed silently. Don't flag their absence; don't suggest creating them upfront.

## File structure

Single-context repo (this repo):

```text
/
├── CONTEXT.md
├── docs/adr/
└── src/
```

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, a test name), use the term as defined in `CONTEXT.md`.

If the concept you need isn't in the glossary yet, note it as a domain-modeling gap.

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding.
