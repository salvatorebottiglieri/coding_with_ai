# Participant Link Access and First Vote Submission

Status: ready-for-agent

## What to build

Deliver an end-to-end participant voting slice where an invited participant opens their unique link (without login), views Proposal details and slots, records yes/no/abstain choices across multiple slots, enters identity fields (name, surname, email), and submits votes with a clear confirmation outcome.

## User stories covered

18, 19, 20, 21, 22

## Acceptance criteria

- [ ] Unique participant link opens a no-login voting page scoped to the correct Proposal version.
- [ ] Voting page shows Proposal title, description, and all current slots with timezone labels.
- [ ] Participant can submit yes/no choices per slot and can mark yes on multiple slots.
- [ ] Participant identity (name, surname, email) is required before successful submission.
- [ ] Successful submission persists votes and returns a confirmation message.
- [ ] Invalid token and malformed submissions return clear error responses.
- [ ] Integration tests cover successful first vote and key validation errors.

## Blocked by

- [OAuth Organizer Flow and Proposal Creation](.scratch/calendar-consensus-app/issues/01-oauth-organizer-flow-and-proposal-creation.md)
