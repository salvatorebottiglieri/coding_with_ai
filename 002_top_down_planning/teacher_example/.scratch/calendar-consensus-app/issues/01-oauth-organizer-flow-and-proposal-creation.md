# OAuth Organizer Flow and Proposal Creation

Status: ready-for-agent

## What to build

Deliver an end-to-end organizer flow where an authenticated organizer signs in with OAuth (Google/Microsoft), creates a Proposal with title, optional description, at least 2 candidate slots, at least 1 participant email, and a deadline, then immediately sees it in the dashboard. Each slot must include an explicit timezone, duplicate participant emails must be deduplicated, and unique participant invitation links must be generated and sent.

## User stories covered

1, 2, 3, 4, 5, 6, 7

## Acceptance criteria

- [ ] Organizer can authenticate via OAuth and access organizer-only create-proposal functionality.
- [ ] Proposal creation validates required inputs (title, 2+ slots, 1+ participant email, deadline) and rejects invalid payloads.
- [ ] Participant emails are deduplicated before invitations are created and sent.
- [ ] Each slot stores explicit timezone metadata and is rendered clearly in organizer views.
- [ ] Unique invitation links are generated per participant and invitation emails are emitted.
- [ ] Newly created Proposal appears in organizer dashboard without manual refresh.
- [ ] Integration tests cover create flow success and validation failures.

## Blocked by

None - can start immediately.
