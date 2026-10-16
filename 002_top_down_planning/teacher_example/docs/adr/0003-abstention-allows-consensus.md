# ADR 0003: Abstention Allows Consensus

## Status
Accepted

## Context
Once a responder has voted on one slot (say, yes on slot A), are they then required to vote on all other slots before those other slots can reach consensus?

- **Must vote everywhere:** Forces every responder to make an explicit decision on every slot. More data, clearer intent, but higher friction.
- **Abstention is OK:** Responders only need to vote on slots they have a strong opinion about. Silence = no objection.

## Decision
If a responder does not vote (abstains) on a slot, it does not block consensus on that slot. Consensus requires all responders to either vote yes or abstain—any explicit no blocks it, but lack of a vote does not.

## Consequences
- **Positive:** Lower barrier to voting. Responders aren't forced to vote on all slots. Reduces decision fatigue.
- **Negative:** A slot with zero yes votes and zero no votes (all abstentions) will reach consensus, which may be unintended.
- **Implementation:** Consensus check: slot passes if at least one responder has yes vote AND zero responders have no votes. Abstained responders are irrelevant.
- **UX:** Voting interface should make abstention (not voting) visually clear as a valid choice.
