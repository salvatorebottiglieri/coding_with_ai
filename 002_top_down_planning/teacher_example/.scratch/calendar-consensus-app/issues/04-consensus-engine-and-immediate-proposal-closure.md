# Consensus Engine and Immediate Proposal Closure

Status: ready-for-agent

## What to build

Deliver consensus evaluation and closure behavior aligned with ADRs: responder unanimity, no-vote veto, abstention allowed, and at-least-one-yes requirement. When consensus is met on a slot, close the Proposal immediately and publish an in-dashboard consensus notification signal for organizer and participants.

## User stories covered

31

## Acceptance criteria

- [ ] Consensus evaluation uses responder-only scope (non-responders do not block).
- [ ] Any explicit no vote vetoes a slot.
- [ ] Abstention does not block a slot, but slot must still have at least one yes vote.
- [ ] On first satisfied slot, Proposal transitions from open to closed_consensus exactly once.
- [ ] Additional votes are rejected once Proposal is closed.
- [ ] Dashboard/banner notification is emitted when consensus is reached.
- [ ] Unit and integration tests cover core consensus edge cases from ADR 0001/0002/0003.

## Blocked by

- [Participant Link Access and First Vote Submission](.scratch/calendar-consensus-app/issues/02-participant-link-access-and-first-vote-submission.md)
