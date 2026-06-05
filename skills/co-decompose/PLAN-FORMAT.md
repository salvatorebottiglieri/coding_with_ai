# Plan File Format

The plan file is a live document updated incrementally during co-decomposition. It captures decisions as they crystallise.

Default filename: `plan.md` (can be overridden by user preference).

## Template

```md
# {Task Title}

## Goal

{One or two sentences: what we are building and why it matters.}

## Scope

### In Scope

- {Feature or capability included}
- {Another included item}

### Out of Scope (explicitly)

- {Feature deliberately excluded}
- {Another excluded item}

## Constraints

- **Technical**: {language, framework, platform, integration constraints}
- **Business**: {stakeholder, compliance, regulatory constraints}
- **Time**: {deadline, milestone, phase constraints}

## User Stories

- As a **{role}**, I want to **{action}** so that **{outcome}**.

## Acceptance Criteria

- {Measurable condition that must be met}
- {Another condition}

## Risks

### Risk: {Name}

- **Likelihood**: {High / Medium / Low}
- **Impact**: {High / Medium / Low}
- **Mitigation**: {How we reduce likelihood or impact}
```

## Rules

- **Be opinionated.** When multiple approaches exist, pick the best one and note briefly why.
- **Keep entries tight.** One or two sentences max per bullet. The plan is a map, not an essay.
- **Show dependencies.** When one decision depends on another, note it explicitly.
- **Flag conflicts.** If a new decision contradicts an earlier one, call it out immediately.
- **Sections can be empty.** A section with no entries is `(none yet)`. Only remove the placeholder when you have something to write.
- **Mark as you go.** Add a `✅` after the section name when the user confirms the section is solid.

## Lifecycle

1. **Goal** is always written first — everything else derives from it
2. **Scope** follows immediately after — defines the boundary
3. **Constraints** crystallise as scope takes shape
4. **User Stories** emerge from goal + scope
5. **Acceptance Criteria** validate the stories
6. **Risks** are surfaced throughout and finalised last
