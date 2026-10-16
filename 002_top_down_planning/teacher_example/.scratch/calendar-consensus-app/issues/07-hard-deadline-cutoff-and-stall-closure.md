# Hard Deadline Cutoff and Stall Closure

Status: ready-for-agent

## What to build

Deliver deadline enforcement and stall lifecycle: server-authoritative hard cutoff rejects at-or-after-deadline votes, and deadline expiry checks close open Proposals to closed_consensus if consensus exists or closed_stall otherwise, with stall summaries for organizer and informational messaging for participants.

## User stories covered

26, 37, 38

## Acceptance criteria

- [ ] Vote submissions at or after deadline are rejected with clear participant feedback.
- [ ] Background deadline evaluation closes open Proposal at cutoff according to consensus outcome.
- [ ] Non-consensus outcome transitions Proposal to closed_stall.
- [ ] Organizer receives stall summary including partial slot support and non-responder list.
- [ ] Participant-facing messaging explains proposal has closed after deadline.
- [ ] Integration tests cover on-time vote acceptance, post-deadline rejection, and stall closure path.

## Blocked by

- [Participant Link Access and First Vote Submission](.scratch/calendar-consensus-app/issues/02-participant-link-access-and-first-vote-submission.md)
