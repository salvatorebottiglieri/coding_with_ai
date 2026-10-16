# ADR 0015: Deadline Is a Hard Cutoff for Votes

## Status
Accepted

## Context
When a proposal deadline arrives, what happens? Should votes received exactly at the deadline second count?

- **Grace period:** Give voters a few seconds past deadline to submit. Reduces friction but adds ambiguity.
- **Hard cutoff:** Deadline time is absolute. Votes before = counted, votes at/after = rejected.
- **Soft close:** System waits 5 minutes past deadline to collect stragglers, then closes.

## Decision
Deadline is a hard cutoff. Votes received before the deadline are counted. Votes at or after the deadline are rejected with an error message. At the deadline moment, the system checks for consensus. If met, proposal closes with consensus. If not, proposal closes with stall state.

## Consequences
- **Positive:** Clear, predictable behavior. No ambiguity about what "deadline" means. Organizer knows exactly when decisions finalize.
- **Negative:** A vote arriving 1 second late is rejected, even if it would have created consensus. Network latency could cause edge-case losses.
- **Implementation:** Server time is authoritative (not client time). Deadline check happens server-side before recording vote. Consensus check runs at deadline + epsilon via cron/background job.
- **UX:** Client shows countdown timer with clear messaging "Voting closes at 5:00 PM EST". Participants receive error message if they try to vote after deadline.
- **Monitoring:** Log vote rejections due to deadline. Alert if consensus calculation is delayed.
