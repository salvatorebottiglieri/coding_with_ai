# Calendar Consensus App — Product Requirements Document

**Status:** ready-for-agent

---

## Problem Statement

Scheduling meetings across multiple participants is tedious and error-prone. Organizers send out availability polls, collect responses across email/chat, negotiate conflicts, and manually create calendar events. Non-responders block progress. There's no clear moment when a decision is finalized, leading to ambiguity and follow-up work.

## Solution

**Calendar Consensus** automates consensus-based scheduling. An organizer proposes a list of candidate time slots and invites participants. Each participant votes on their availability via a unique link (no login required). When all **active responders** agree on the same slot, the system automatically creates a Google Calendar event and notifies everyone. If no consensus is reached by the deadline, the organizer can review results and decide next steps.

Key behaviors:
- Non-responders don't block consensus (only active voters count)
- "No" votes are vetoes (block that slot entirely)
- Participants can change votes up to 3 times
- Organizer can dynamically remove participants and add/remove time slots
- Hard deadline cutoff; votes after deadline are rejected
- All time slots include explicit timezone; participants see multi-timezone conversions

---

## User Stories

### Organizer: Creating Proposals

1. As an organizer, I want to authenticate via OAuth (Google/Microsoft) so that I can securely access the app without managing passwords.

2. As an organizer, I want to create a new proposal by entering: title, description, list of candidate time slots (min 2), participant email list (min 1), and a deadline so that I can initiate the scheduling process.

3. As an organizer, I want the system to deduplicate email addresses in the participant list so that I don't accidentally invite the same person twice.

4. As an organizer, I want each time slot to require me to specify a timezone so that participants across time zones see clear, unambiguous times.

5. As an organizer, I want to see the proposal appear in my dashboard immediately after creation so that I can monitor responses in real time.

6. As an organizer, I want the system to automatically generate and send unique invitation links to each participant so that they can vote without logging in.

7. As an organizer, I want to invite myself as a participant on my own proposals so that my availability votes count toward consensus.

### Organizer: Monitoring and Managing

8. As an organizer, I want to see a real-time vote matrix (responders × slots, auto-refreshing every 5 seconds) showing names, emails, response status, and yes/no/abstain votes so that I have full visibility into the voting state.

9. As an organizer, I want to see which participants have not yet responded so that I can follow up with them before consensus is reached.

10. As an organizer, I want to add new time slots to an active proposal (appearing in real-time to responders) so that I can adapt to schedule changes without restarting.

11. As an organizer, I want to remove time slots from a proposal (and discard all votes on those slots) so that I can eliminate options that no longer work.

12. As an organizer, I want to remove specific participants from a proposal (and discard their votes) so that I can adapt if someone becomes unavailable.

13. As an organizer, I want consensus to be recalculated automatically after I remove a participant, and to create a calendar event if consensus is suddenly reached, so that the process is seamless.

14. As an organizer, I want to extend the proposal deadline so that I can give more time for responses if needed.

15. As an organizer, I want to manually close a proposal before the deadline so that I can finalize decisions early if consensus exists.

16. As an organizer, I want to reopen a closed proposal with new slots and/or deadline (creating a new version), so that I can retry scheduling without starting from scratch.

17. As an organizer, I want to see the proposal's version history and know which version participants are voting on so that there's no confusion.

### Participant: Voting

18. As a participant, I want to click a unique link and be taken to a voting page (no login required) showing the proposal title, description, and all available time slots so that I can quickly understand what I'm voting on.

19. As a participant, I want to indicate my availability on each time slot by clicking yes/no (or leaving it blank for abstention) so that I can express my schedule constraints clearly.

20. As a participant, I want to select "yes" on multiple slots simultaneously so that I can indicate I'm flexible across multiple options.

21. As a participant, I want to enter my name, surname, and email before submitting so that the organizer knows who responded.

22. As a participant, I want to see a confirmation message after submitting my votes so that I know my response was recorded.

23. As a participant, I want to click my unique link at any time before the deadline to change my votes so that I can update my availability as my schedule changes.

24. As a participant, I want the system to show me how many vote changes I have remaining (max 3) so that I can plan my final decision carefully.

25. As a participant, I want my votes to be locked after 3 changes so that I'm committed to a decision and prevent chaotic flip-flopping.

26. As a participant, I want to see a clear message if I try to vote after the deadline so that I understand why my response was rejected.

27. As a participant, I want to see timezone conversion helpers (hover/click to see equivalent times in other timezones) so that I can accurately evaluate slots in my local time.

28. As a participant, I want the Google Calendar event (if created) to display in my local timezone so that I don't miss the meeting due to timezone confusion.

### Participant: Reopened Proposals

29. As a participant, I want to receive a new invitation link if a proposal is reopened with new slots/deadline so that I can vote again with a fresh vote budget.

30. As a participant, I want to see a message if I click an old link to a closed or updated proposal, with a link to the latest version if one exists, so that I don't get confused about which version to vote on.

### Consensus and Event Creation

31. As an organizer/participant, I want to receive real-time notification (in-dashboard banner) when consensus is reached so that I know the meeting is decided.

32. As an organizer, I want the system to automatically create a Google Calendar event on my calendar when consensus is reached, with all invited participants (including non-responders) so that the meeting is booked.

33. As an organizer, I want the event title, date/time (in my timezone), and attendee list to match exactly what was agreed so that there are no misunderstandings.

34. As all participants, I want to receive an email notification when consensus is reached, with event details and a calendar invite, so that I'm aware and can add it to my calendar.

35. As an organizer, I want the system to retry Google Calendar creation up to 3 times if the API fails, then enter state `closed_consensus_creation_failed` and email me manual creation details, so that I can still create the event if the API is down.

36. As an organizer, I want only I (not participants) to receive the failure email, so that participants aren't confused by technical issues.

### Stall State and Reopening

37. As an organizer, I want to receive an email when the deadline expires without consensus, showing which slots have partial support and who didn't respond, so that I can make an informed decision about next steps.

38. As an organizer, I want the option to cancel the proposal, reopen it with new slots/deadline, or manually select a slot and proceed, so that I have flexibility when consensus fails.

---

## Implementation Decisions

### Proposal State Machine

Proposals move through states in a forward-only direction:
- `open` → `closed_consensus` (consensus reached, event created successfully)
- `open` → `closed_consensus_creation_failed` (consensus reached, Google Calendar failed after 3 retries)
- `open` → `closed_stall` (deadline passed, no consensus)

Reopening a closed proposal creates a new version (immutable history). Old versions are archived.

**Rationale:** (See ADR 0012) Immutable audit trail. Participants vote on new versions. No temporal ambiguity.

### Consensus Logic

**Consensus is reached when:**
- All responders (participants who have clicked and voted at least once) agree on the same time slot
- Non-responders (invited but never clicked) do NOT block consensus
- Abstention (not voting on a slot) does NOT block consensus
- **Any "no" vote on a slot blocks that slot entirely** (veto semantics)

**Formally:** A slot S reaches consensus iff:
- At least one responder voted yes on S
- Zero responders voted no on S
- (Abstentions are ignored)

**Rationale:** (See ADRs 0001, 0002, 0003) Enables timely decisions. Respects explicit unavailability. Doesn't penalize silence.

### Vote Change Limits

Each responder gets **exactly 3 vote changes per proposal version**. After the 3rd change, their votes lock and become immutable until proposal closes.

One change = one save action across all slots (atomic).

**Rationale:** (See ADR 0006) Encourages thoughtful voting while allowing corrections. Prevents chaotic flip-flopping.

### Participant Dynamics

Organizers can **remove participants after proposal creation**. Removed votes are discarded; consensus is recalculated. If consensus now exists, the event is created automatically.

Organizers **cannot** add participants after creation (they'd miss deadline anyway). Participants cannot be modified during consensus check—changes only persist if vote is accepted.

**Rationale:** (See ADRs 0007, 0008) Flexibility for real-world changes without breaking consensus math for long.

### Time Slot Management

Organizers can **add and remove time slots** after proposal creation.
- New slots appear in real-time for responders (no new notifications)
- Removed slots discard all votes on them; consensus is recalculated
- Can trigger consensus if a veto slot is removed

Slots store: `datetime`, `timezone_id` (IANA tz database)

**Rationale:** (See ADR 0009) Flexibility for evolving schedules.

### Deadline Behavior

**Hard cutoff:** Votes received before deadline are counted. Votes at or after deadline are rejected.

At deadline expiry, system checks for consensus. If met → `closed_consensus`. If not → `closed_stall`.

Server time is authoritative (not client). Background job checks at deadline + epsilon.

**Rationale:** (See ADR 0015) Clear, predictable semantics. No ambiguity.

### Google Calendar Integration

When consensus is reached:
1. System attempts to create event on organizer's Google Calendar
2. Event includes: title, start time (in organizer's timezone), attendees (all invited + non-responders)
3. Retries up to 3 times on failure
4. If all retries fail → state `closed_consensus_creation_failed`, email to organizer only

**Rationale:** (See ADR 0010) Consensus is logically final. Organizer can manually create if needed. Participants not spammed about backend failures.

### Authentication & Authorization

- **Organizers:** OAuth (Google, Microsoft). Session timeout: 30 days inactivity.
- **Participants:** No login. Unique versioned links: `https://.../vote/{proposal_id}/{version}/{token}`

Old links show redirect message with latest version link.

**Rationale:** (See ADR 0014) Familiar auth. No participant friction. Versioned links prevent accidental voting on old versions.

### Timezone Handling

Organizers specify timezone for each slot (default: their account timezone).

UI shows: `2:00 PM EST` + hover/click conversion to other timezones.

Google Calendar events created in organizer's timezone; participants' devices auto-display locally.

**Rationale:** (See ADR 0016) Single source of truth (organizer TZ). Clear for all. Google Calendar handles device display.

### Email Notifications

Sent to:
- **Organizer** on: invitation accepted, consensus reached, deadline expired (stall), Google Calendar failure
- **Participants** on: invited (initial + reopened versions), consensus reached, deadline expired (informational)

Only organizer receives technical failure emails (Google Calendar).

---

## Testing Decisions

### What Makes a Good Test

A good test validates **external behavior** (inputs → outputs), not implementation details:
- ✅ Test that consensus is calculated correctly given a set of votes
- ❌ Don't test internal helper function `calculate_available_responders()`
- ✅ Test that removing a participant triggers consensus if votes now align
- ❌ Don't test the database query used to fetch participant votes
- ✅ Test that votes submitted after deadline are rejected
- ❌ Don't test the internal `compare_timestamps()` logic

### Testing Seams

**Seam 1: Proposal Aggregate (Domain)**
- Core domain logic: consensus calculation, state transitions, vote tracking
- Tests: unit tests + integration tests at aggregate boundary
- External dependencies mocked: persistence, calendar API, email service

**Seam 2: Proposal Lifecycle (Application)**
- Full end-to-end flows: create → vote → consensus → event creation → notification
- Tests: integration tests; use real domain aggregate, mock only I/O (calendar, email)
- Scenarios: happy path, participant removal triggering consensus, deadline stall, Google Calendar failures

**Seam 3: Participant Voting API (Application)**
- Vote submission, vote change limit enforcement, deadline cutoff
- Tests: integration tests with mocked persistence + auth
- Scenarios: successful vote, 3rd change locks votes, post-deadline rejection, vote change budget display

**Seam 4: Calendar & Notification Services (Infrastructure)**
- Google Calendar event creation (retries, failure states)
- Email sending (confirmation, consensus, stall, failure notifications)
- Tests: unit tests + integration tests with service mocks
- Prior art: existing Google Calendar integrations in codebase (if any)

### Modules to Test

1. `ProposalAggregate` (domain) — consensus logic, state machine, vote accounting
2. `ProposalService` (application) — proposal lifecycle, consensus trigger, participant removal
3. `VotingService` (application) — vote submission, vote change limits, deadline validation
4. `CalendarService` (infrastructure) — Google Calendar event creation, retries, error handling
5. `NotificationService` (infrastructure) — email sending, template rendering

### Test Structure

- **Unit tests:** Aggregate logic, timezone conversions, consensus calculations
- **Integration tests:** Proposal creation → voting → consensus → event creation → email (happy path + error scenarios)
- **Contract tests:** Google Calendar API mocks, email service mocks (verify payloads)

### Example Test Scenarios

- Organizer creates proposal with 3 slots, 3 participants
- Participant A votes yes on slots 1 & 2, Participant B votes yes on slot 1 only, Participant C never responds
- Expected: Consensus NOT reached (B abstained on slot 2, so slot 1 has only 2 yes)
- Organizer removes Participant C (non-responder)
- Expected: Consensus STILL not reached (B's votes unchanged)
- Organizer removes Participant B's no vote on slot 2 (by removing B)
- Expected: Consensus reached on slot 2 (A and C abstain, 0 no votes). Event created. Email sent.

---

## Out of Scope

- **User accounts/profile management** (beyond OAuth)
- **Calendar integrations other than Google Calendar** (Microsoft Outlook, Apple Calendar APIs out of scope; participants can sync via calendar invite)
- **Mobile app** (web-only; responsive design for mobile browsers)
- **Recurring meetings** (one-off proposals only)
- **Timezone auto-detection** (organizer must specify; participants set their own device timezone)
- **Proposal templates** (no copy/paste proposals)
- **Undo/restore deleted proposals** (deletion is permanent; reopening creates new version)
- **Proposal sharing** (organizer must manually send links)
- **Waitlist/alternative dates** (if stall, organizer reruns proposal)
- **Integration with meeting notes/agendas** (calendar event only)
- **Participant feedback/scoring** (yes/no only; no ranking)

---

## Further Notes

### Architecture Considerations

- **No participant database** until they vote (no pre-registration required)
- **Immutable versions:** Old proposals never change. Reopening creates new version with fresh link tokens.
- **Background jobs:** Deadline expiry check, Google Calendar retry queue
- **Real-time updates:** Dashboard uses WebSocket or polling (5-second cadence) for vote matrix
- **Audit trail:** All state transitions logged. Google Calendar state tracked (pending, success, failed).

### Future Enhancements (Post-MVP)

- Slack/Teams notifications
- Proposal analytics (response rates, most popular slots)
- Bulk proposal creation from calendar
- Participant feedback loop ("I can't make this time, suggest alternatives")
- Proposal sharing links (view-only for organizer's team)
- Time zone detection from participant's calendar/device

### Glossary Reference

See [CONTEXT.md](../../CONTEXT.md) for domain terminology:
- **Proposal** — the scheduling request (proposta)
- **Organizer** — creator, authenticated user
- **Invited Participant** — person on participant list
- **Responder** — invited person who voted ≥1 time
- **Non-responder** — invited but never clicked link
- **Consensus** — all responders agree on same slot
- **Vote** — yes/no/abstain on a slot; max 3 changes
- **Stall** — deadline expires without consensus

### Architectural Decisions

See [docs/adr/](../../docs/adr/) for detailed trade-off analysis:
- ADR 0001: Responder unanimity (not global unanimity)
- ADR 0002: "No" vote is veto
- ADR 0003: Abstention allows consensus
- ADR 0007: Dynamic participant removal
- ADR 0010: Google Calendar failure handling
- ADR 0012: Forward-moving state machine + versioning
- ADR 0014: OAuth authentication + versioned links
- ADR 0015: Hard deadline cutoff
- ADR 0016: Timezone handling
