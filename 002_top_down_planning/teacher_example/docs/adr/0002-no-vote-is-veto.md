# ADR 0002: "No" Vote Is a Veto

## Status
Accepted

## Context
When a responder votes on a time slot, they can indicate "yes" (available) or "no" (unavailable). The question is: what does a "no" vote mean?

- **Soft no:** A no vote expresses preference, but if everyone else says yes, the slot can still reach consensus.
- **Hard veto:** A no vote blocks the slot from ever reaching consensus.

Respecting explicit unavailability is important—we shouldn't schedule people into times they said no to.

## Decision
A "no" vote on a slot acts as a veto. That slot cannot reach consensus if any responder votes no on it, regardless of how many others said yes.

## Consequences
- **Positive:** Respects explicit unavailability. No one gets scheduled into a time they said no to.
- **Negative:** A single person blocking a slot could prevent consensus entirely (though organizer can remove that person).
- **Implementation:** Consensus check must return false if any responder has a no vote on the candidate slot.
- **UX:** Dashboard should highlight slots with vetoes, and show which responder vetoed them.
