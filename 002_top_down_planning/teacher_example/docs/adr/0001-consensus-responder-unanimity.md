# ADR 0001: Consensus Requires Responder Unanimity, Not Global Unanimity

## Status
Accepted

## Context
When scheduling a meeting via proposal, participants are invited and asked to vote on availability. Some invited people may never respond (non-responders). The question is: for consensus to be reached, must **all invited participants** agree, or only **all participants who have actively voted**?

- **All invited** approach: Prevents the meeting from being scheduled if anyone ignores the invite. Risk of indefinite waiting.
- **All responders** approach: Respects those who engage, treats silence as abstention. Enables timely decisions.

## Decision
Consensus is reached when **all responders agree on the same time slot**. Non-responders do not block consensus. The calendar event is created even if some invited people never voted.

## Consequences
- **Positive:** Meetings get scheduled in a reasonable timeframe. Silent non-responders don't prevent forward progress.
- **Negative:** Some invited people might miss the meeting because they didn't vote but still got invited to the calendar event.
- **Implementation:** Consensus calculation must distinguish invited (total) vs. responders (voted). Dashboard shows both clearly.
- **UX:** Organizer dashboard must highlight non-responders so organizer can follow up if needed before consensus is reached.
