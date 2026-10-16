# Vote Matrix Visibility with Live Response Status

Status: ready-for-agent

## What to build

Deliver organizer visibility for active Proposals through a real-time vote matrix that shows responders, non-responders, participant identities, and per-slot vote states with a 5-second refresh cadence, so organizers can monitor progress and follow up on missing responses.

## User stories covered

8, 9

## Acceptance criteria

- [ ] Organizer dashboard shows a responders x slots matrix for active Proposals.
- [ ] Matrix exposes participant name, email, and response status (responder vs non-responder).
- [ ] Vote state is visible per participant per slot (yes/no/abstain/blank).
- [ ] Dashboard updates on a 5-second cadence (polling or push equivalent) and reflects recent submissions.
- [ ] Non-responders are clearly identifiable for follow-up.
- [ ] Integration tests verify matrix correctness and refresh behavior.

## Blocked by

- [Participant Link Access and First Vote Submission](.scratch/calendar-consensus-app/issues/02-participant-link-access-and-first-vote-submission.md)
