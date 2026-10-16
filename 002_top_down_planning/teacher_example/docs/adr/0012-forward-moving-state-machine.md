# ADR 0012: Proposal States Are Forward-Moving; Reopening Creates a New Version

## Status
Accepted

## Context
A proposal has a lifecycle: created (open) → reaches consensus or deadline expires (closed). What happens if an organizer wants to reopen a closed proposal with new slots or extended deadline?

- **Mutate existing proposal:** Simpler data model, but breaks audit trail and creates temporal confusion (which slots/deadline are active now?).
- **Create a new version:** Immutable history, clear lineage, but more complex data model and participants get new invites.

## Decision
Proposal states move forward only: `open` → `closed_consensus`, `closed_stall`, or `closed_consensus_creation_failed`. When an organizer reopens a closed proposal, the system creates a new proposal version with state = `open`. Old versions remain immutable.

## Consequences
- **Positive:** Immutable audit trail. Future readers understand exactly what happened and when. No temporal ambiguity.
- **Negative:** More complex data model. Participants need to vote on new version (old votes don't carry forward). More invites sent.
- **Implementation:** Each proposal has `version` field and `parent_proposal_id` (points to previous version if reopened). State machine only allows forward transitions.
- **Data:** Old proposals are archived but never deleted. Dashboard can show proposal history/lineage.
- **UX:** When organizer reopens, they're shown it's a new version and participants will receive new invites with fresh vote budgets.
