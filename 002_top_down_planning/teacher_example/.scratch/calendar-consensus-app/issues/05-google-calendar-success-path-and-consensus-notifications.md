# Google Calendar Success Path and Consensus Notifications

Status: ready-for-agent

## What to build

Deliver the successful post-consensus integration path: when a Proposal reaches closed_consensus, create the Google Calendar event in organizer context using winner slot details and include all invited participants (including non-responders), then notify organizer and participants with event details.

## User stories covered

32, 33, 34

## Acceptance criteria

- [ ] Consensus winner triggers Google Calendar event creation with correct title, date/time, timezone, and attendee list.
- [ ] Event payload preserves organizer timezone source-of-truth and remains display-safe for participant local time rendering.
- [ ] Organizer receives confirmation notification containing event details.
- [ ] Participants receive consensus-reached notification containing event details/invite metadata.
- [ ] Event creation and notification dispatch are idempotent against duplicate consensus triggers.
- [ ] Integration tests verify payload correctness and notification fan-out.

## Blocked by

- [Consensus Engine and Immediate Proposal Closure](.scratch/calendar-consensus-app/issues/04-consensus-engine-and-immediate-proposal-closure.md)
