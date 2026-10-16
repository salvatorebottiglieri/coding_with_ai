# Organizer Live Management of Slots and Participants

Status: ready-for-agent

## What to build

Deliver organizer management actions on active Proposals from the dashboard: add/remove slots, remove participants (with vote discard), extend deadline, and manual close. Each mutation must trigger immediate consensus recalculation and real-time UI updates, including auto-transition when consensus becomes satisfied after removals.

## User stories covered

10, 11, 12, 13, 14, 15

## Acceptance criteria

- [ ] Organizer can add slots with explicit timezone to an open Proposal and responders can see updates in near real-time.
- [ ] Organizer can remove slots; associated votes are discarded and consensus is recalculated.
- [ ] Organizer can remove participants; participant votes are discarded and consensus recalculates immediately.
- [ ] If participant/slot removal causes consensus, Proposal auto-transitions through standard consensus closure path.
- [ ] Organizer can extend deadline and manually close open Proposal from dashboard controls.
- [ ] Integration tests cover mutation side effects, recalculation triggers, and state consistency.

## Blocked by

- [Vote Matrix Visibility with Live Response Status](.scratch/calendar-consensus-app/issues/03-vote-matrix-visibility-with-live-response-status.md)
- [Consensus Engine and Immediate Proposal Closure](.scratch/calendar-consensus-app/issues/04-consensus-engine-and-immediate-proposal-closure.md)
