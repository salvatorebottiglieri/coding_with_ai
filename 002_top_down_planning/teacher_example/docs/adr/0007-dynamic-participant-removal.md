# ADR 0007: Organizer Can Add/Remove Participants Dynamically

## Status
Accepted

## Context
After a proposal is created and invites sent, real-world situations change: someone becomes unavailable, or organizer realizes they missed someone. Should the organizer be able to modify the participant list mid-proposal?

- **Immutable participant list:** Prevents consensus math breakage. Once sent, the decision framework is locked.
- **Mutable list:** Provides flexibility. Organizer can adapt to changing circumstances.

If mutable, removing a participant who voted "no" could suddenly enable consensus on previously blocked slots—is that OK?

## Decision
The organizer can remove participants after proposal creation. When a participant is removed, their votes are discarded and consensus is recalculated immediately. If consensus is newly met on any slot, the event is created automatically.

## Consequences
- **Positive:** Real-world flexibility. Organizer can adapt without creating a new proposal. Removing a veto-holder enables consensus.
- **Negative:** Consensus math changes dynamically. A slot might go from blocked to consensus in an instant. Participants don't get re-invited when added.
- **Implementation:** Participant removal triggers consensus recalculation. If new consensus exists, event creation is triggered.
- **UX:** Organizer dashboard must show participant removal actions with clear confirmations. Real-time consensus status updates.
- **Note:** Adding new participants is risky (they might miss deadline), so may not be supported or requires manual re-invites.
