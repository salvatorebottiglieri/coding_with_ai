# Reopen as New Version with Link Rotation and History

Status: ready-for-agent

## What to build

Deliver forward-only Proposal lifecycle reopening: closed Proposals can be reopened only by creating a new immutable version with fresh participant links and fresh vote-change budgets, while old links show clear stale-version messaging and route users to latest version when available. Provide organizer-visible version lineage/history.

## User stories covered

16, 17, 29, 30

## Acceptance criteria

- [ ] Reopen action on closed Proposal creates a new open version rather than mutating old version.
- [ ] New version receives new participant link tokens and resets participant vote-change budgets.
- [ ] Old version links show clear message that version is closed/updated and provide latest-version path when available.
- [ ] Organizer can see version history/lineage to distinguish active and archived versions.
- [ ] Votes and state transitions remain immutable on closed versions.
- [ ] Integration tests validate reopen lineage, link rotation behavior, and stale-link messaging.

## Blocked by

- [Hard Deadline Cutoff and Stall Closure](.scratch/calendar-consensus-app/issues/07-hard-deadline-cutoff-and-stall-closure.md)
- [Organizer Live Management of Slots and Participants](.scratch/calendar-consensus-app/issues/08-organizer-live-management-of-slots-and-participants.md)
