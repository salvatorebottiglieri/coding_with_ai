# Calendar Failure Retries and Creation-Failed State

Status: ready-for-agent

## What to build

Deliver failure-handling behavior for Google Calendar integration: retry creation up to 3 attempts with backoff, then transition to closed_consensus_creation_failed and notify organizer only with manual event creation details, while preserving forward-only state semantics.

## User stories covered

35, 36

## Acceptance criteria

- [ ] Google Calendar failures trigger retry policy capped at 3 attempts.
- [ ] After exhausted retries, Proposal transitions to closed_consensus_creation_failed and remains closed.
- [ ] Failure email is sent only to organizer with actionable manual event details (title, slot, attendees, timezone).
- [ ] Participants do not receive technical failure email.
- [ ] System records failure reason and attempts for audit/observability.
- [ ] Integration tests verify retry cap, terminal state transition, and organizer-only email behavior.

## Blocked by

- [Google Calendar Success Path and Consensus Notifications](.scratch/calendar-consensus-app/issues/05-google-calendar-success-path-and-consensus-notifications.md)
