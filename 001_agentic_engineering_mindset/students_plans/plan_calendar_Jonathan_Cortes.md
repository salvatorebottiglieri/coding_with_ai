# Calendar Consensus App — Planning Document

## Goal
Build an app that helps groups schedule events through consensus:
- Participants submit their available time slots (when they're free)
- Organizer reviews all submissions and picks one or more slots as the final meeting time
- Participants confirm or decline attendance for the organizer's final selection

## Scope
**In MVP:**
- Specific time slots (e.g., "Tuesday 2-3pm")
- Participants submit their available time slots
- Organizer reviews all submissions and picks one or more slots as the final meeting time
- Participants confirm or decline attendance for the organizer's final selection
- Link-based participation (shareable URL)
- Email invites with link as fallback
- Internal meetings (same timezone) and external meetings (different timezones)

**Out (Future):**
- Time ranges (e.g., "Tuesday 2-5pm")
- Automatic conflict detection
- Recurring events

## Constraints
- Two meeting types: internal (same timezone) and external (different timezones)
- Participants can change availability after submitting
- **Availability threshold: 75%** — if a selected slot drops below this, organizer gets options:
  1. Keep the selection
  2. Send warning to participants about the drop
  3. Pick a different date
- Calendar integrations: Google Calendar and Outlook (read availability + sync final event)
- Team size: TBD

## User Stories

**Story 1: Organizer creates a meeting**
- As an organizer, I want to create a new meeting and set basic details (title, description), so I can invite participants to submit their available time slots

**Story 2: Organizer sends invites**
- As an organizer, I want to send invitation links and emails to participants, so they can access the scheduling page

**Story 3: Participant submits available slots**
- As a participant, I want to see the meeting details and submit one or more time slots when I'm available, so the organizer can find overlaps

**Story 4: Participant updates availability**
- As a participant, I want to change my submitted availability after submitting, so I can keep my response up-to-date with my calendar

**Story 5: Organizer reviews submissions**
- As an organizer, I want to see all submitted time slots ranked by participant availability (%), so I can identify the best times

**Story 6: Organizer picks final meeting time(s)**
- As an organizer, I want to select one or more time slots as the final meeting time(s) and receive feedback if availability drops below 75%, so I can finalize the meeting confidently

**Story 7: Participants confirm attendance**
- As a participant, I want to confirm or decline the organizer's final time(s), so everyone knows who's attending

**Story 8: Calendar sync (Future)**
- As a user, I want the final event to sync to my Google Calendar or Outlook, so it appears in my calendar system

## Acceptance Criteria

**Story 1 — Organizer creates meeting:**
- [ ] Organizer can enter meeting title, description, and select internal or external (timezone)
- [ ] System generates unique shareable link
- [ ] Organizer can copy link to clipboard
- [ ] Meeting is created and ready to accept proposals

**Story 2 — Organizer sends invites:**
- [ ] Organizer can enter participant email addresses
- [ ] Email sent with shareable link and meeting details
- [ ] Participants can access the link without registration

**Story 3 — Participant proposes slots:**
- [ ] Participant can view meeting details (title, description, timezone info)
- [ ] Participant can add one or more specific time slots (date + start/end time)
- [ ] Slots are validated (no overlaps, valid times)
- [ ] Submission is confirmed visually

**Story 4 — Participant updates availability:**
- [ ] Participant can view their previously submitted slots
- [ ] Participant can add new slots, remove existing ones, or clear all
- [ ] Changes are saved and reflected in organizer's dashboard immediately
- [ ] Participant receives confirmation of changes

**Story 5 — Organizer reviews proposals:**
- [ ] Organizer sees all proposed slots sorted by availability % (highest first)
- [ ] Each slot shows: date, time, number of people available, % of total participants
- [ ] Organizer can see who is/isn't available for each slot
- [ ] Timezone is displayed (if external meeting)

**Story 6 — Organizer makes final selection:**
- [ ] Organizer can select one or more slots as "final"
- [ ] If any slot drops below 75% availability, system alerts organizer with three options:
  - Keep selection + send warning to participants
  - Keep selection without warning
  - Choose a different date
- [ ] Selected date(s) marked as "confirmed"

**Story 7 — Participants confirm attendance:**
- [ ] Participants notified (email + app notification) of organizer's final selection
- [ ] Participants can confirm "yes", "no", or "maybe" for each selected date
- [ ] Organizer can see final RSVP counts

**Story 8 — Calendar sync:**
- [ ] Final confirmed event can be exported to Google Calendar / Outlook
- [ ] Event appears in user's calendar with all attendees

## Risks

| Risk | Impact | Mitigation |
|------|--------|-----------|
| **Timezone display confusion** — External participants see times in wrong timezone | High | Auto-detect user timezone; show times in both local + meeting timezone |
| **Email deliverability** — Invites land in spam or bounce | High | Use professional email service (SendGrid, AWS SES); add whitelisting docs |
| **Participants don't update availability** — Organizer selects date but people become unavailable | Medium | Send reminder emails asking participants to confirm current availability |
| **Organizer doesn't notice availability drop below 75%** — Selects slot that falls to 60% due to withdrawals | Medium | Make warning prominent (modal/banner); don't allow selection until threshold met |
| **Calendar integration fails** — Google/Outlook auth breaks or sync doesn't work | Medium | Graceful fallback: allow manual export (ICS file) if auth fails |
| **Concurrent changes** — Participant updates availability while organizer is selecting | Medium | Use optimistic updates + refresh data when organizer makes selection |
| **Ghost participants** — Email invites sent to inactive emails; people never respond | Low | Organizer can manually mark participants as "no response" after deadline |
| **Large team scalability** — App slows down with 100+ participants and 50+ proposed slots | Medium | Paginate/filter slot lists; index by participant count |
| **Meeting link shared publicly** — Sensitive meetings exposed online | Medium | Add optional password protection for private meetings |
| **Ambiguous time slot format** — "Tuesday 2pm" could mean different things | Low | Use ISO 8601 format + explicit timezone in UI |
