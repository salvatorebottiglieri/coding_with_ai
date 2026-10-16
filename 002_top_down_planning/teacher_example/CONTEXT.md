# Calendar Consensus — Domain Model

## Ubiquitous Language

### Proposal (Proposta)
A scheduling request created by an organizer. Contains:
- Title, description, deadline
- List of candidate time slots
- Set of invited participants
- Current state (open, closed_consensus, closed_stall)

### Organizer
The person who creates a proposal. Authenticated user. Responsible for:
- Setting up the proposal (title, slots, participants, deadline)
- Monitoring responses in real-time on the dashboard
- Deciding next steps if stall occurs (cancel, reopen, manually select)

**Important:** The organizer can also invite themselves as a participant on their own proposal. If they do, their votes count toward consensus like any other responder.

### Invited Participant
A person the organizer added to the proposal's participant list. They receive an invitation email with a unique link. May or may not respond.

### Responder
An invited participant who has clicked their link and cast at least one vote (yes/no on any slot). Non-responders are those who never clicked the link.

### Consensus
The moment when **all responders agree on the same time slot**. Non-responders do not block consensus. Consensus can occur before the deadline. When reached:
- Proposal closes immediately
- Calendar event is created (invited to all originally invited participants, including non-responders)
- Notifications sent to organizer and all participants

### Stall (Stallo)
When the deadline expires and no slot has unanimous support from all responders. The proposal closes without a consensus event. Organizer must manually decide: cancel, reopen with new slots, or pick a slot manually.

### Vote
A responder's indication of availability (yes/no) on a specific slot. One responder can vote yes on multiple slots simultaneously. Votes can be changed until the proposal closes.
- **Yes vote:** Indicates availability on that slot. Counts toward consensus if all responders say yes.
- **No vote:** Blocks consensus on that slot (acts as a veto), even if all others said yes.
- **Abstention:** Not voting on a slot. Does not block consensus; slot can reach consensus if all other responders say yes.

## Key Distinctions

| Concept | Definition |
|---------|-----------|
| **Invited** | Person on the original participant list at proposal creation |
| **Responder** | Invited person who clicked the link and voted (at least once) |
| **Consensus** | Every responder votes yes on the same slot (responder unanimity, not global unanimity) |
| **Non-responder** | Invited but never clicked link; does not block consensus |

## Decision Log

**D1: Consensus requires responder unanimity, not global unanimity**  
*Decision:* Consensus is reached when all participants who have actively voted (responders) agree on the same slot. Non-responders do not block consensus.  
*Rationale:* Prevents indefinite waiting for non-responders. Responder agreement is sufficient to create the meeting.  
*Implication:* Calendar event is created even if some invited people never responded.

**D2: "No" vote is a veto**  
*Decision:* If any responder votes "no" on a slot, that slot cannot reach consensus even if everyone else voted yes.  
*Rationale:* Respects the intent of saying "unavailable"—prevents scheduling meetings at times people explicitly reject.  
*Implication:* Consensus requires all responders to either vote yes or abstain (not vote) on a slot; any explicit no blocks it.

**D3: Abstention allows consensus**  
*Decision:* If a responder does not vote (abstains) on a slot, it does not block consensus on that slot.  
*Rationale:* Responders are not forced to vote on all slots. Only explicit "no" votes veto a slot. Abstention = no objection.  
*Implication:* Consensus on a slot requires all responders to either vote yes or abstain—at least one yes vote, and zero no votes.

**D4: Organizer can participate and vote**  
*Decision:* An organizer can invite themselves to their own proposal's participant list. Their votes count toward consensus.  
*Rationale:* Avoids special-casing organizers. Organizers often need to attend their own meetings and should have a voice in scheduling.  
*Implication:* If the organizer is on the participant list and votes "no" on all slots, consensus cannot be reached unless they later say yes to something.

**D5: No minimum responders for consensus**  
*Decision:* Consensus can be reached with any number of responders (including 1). "All responders" means whoever has voted.  
*Rationale:* Simplicity. If someone invites only themselves or only 1 other person, a yes vote should trigger consensus.  
*Implication:* A proposal with 1 invited person reaching consensus is valid. The event is created and notifications sent.

**D6: Votes can be changed, max 3 times per responder**  
*Decision:* Each responder gets 3 total vote changes per proposal. After the 3rd change, votes are locked and cannot be modified further.  
*Rationale:* Allows for corrections and mind changes while preventing chaotic flip-flopping. Encourages thoughtful voting.  
*Implication:* UI must track and display remaining change budget. When limit is reached, voting interface becomes read-only. Change is atomic (one save = one change).

**D7: Organizer can add/remove participants dynamically with consensus recalculation**  
*Decision:* After a proposal is created, the organizer can remove participants. When a participant is removed, their votes are discarded and consensus is recalculated against the remaining responders.  
*Rationale:* Flexibility for real-world scenarios (someone becomes unavailable, organizer wants to shrink the meeting). Dynamic recalculation keeps the proposal valid.  
*Implication:* Removing a participant can suddenly enable consensus if they were blocking a slot with a "no" vote.

**D8: Consensus auto-triggers after participant removal**  
*Decision:* When the organizer removes a participant, the system immediately recalculates consensus. If consensus is now met on any slot, the calendar event is created automatically.  
*Rationale:* Seamless UX—no extra manual steps. The decision was logically possible before (votes were there), so respecting it immediately makes sense.  
*Implication:* Organizer sees real-time notifications when removal causes consensus to trigger.

**D9: Time slots are mutable (add/remove) with real-time updates and consensus recalculation**  
*Decision:* Organizers can add new time slots and remove existing ones after proposal creation. New slots appear in real-time to responders; no new notifications sent. Removed slots discard all votes on them and trigger consensus recalculation.  
*Rationale:* Adds flexibility for evolving schedules. Real-time UI keeps responders seeing current state without notification spam.  
*Implication:* Removing a slot can cascade—if it was the only slot all responders agreed on, removing it prevents consensus. Conversely, removing a slot with a veto ("no" vote) might enable consensus on other slots.

**D10: Google Calendar creation failure handling**  
*Decision:* If Google Calendar creation fails after 3 retries, the proposal enters state `closed_consensus_creation_failed`. Email notification goes to organizer only with event details for manual creation. Proposal stays locked and does not reopen.  
*Rationale:* Consensus is logically finalized—don't revert it. Organizer has the data to manually create the event if needed. Single email to organizer avoids spamming participants about a backend failure.  
*Implication:* Participants see "event will be added to calendar" in the consensus notification even if it later fails; organizer must notify them if needed.

**D11: Email deduplication at proposal creation**  
*Decision:* If the organizer enters duplicate email addresses in the participant list, the system deduplicates at creation time. Only unique emails receive invites. Consensus math is based on unique responders.  
*Rationale:* Prevents accidental double-invitations and confusion. Simplifies the data model.  
*Implication:* If organizer adds alice@example.com twice, she gets 1 link and counts as 1 responder for consensus (not 2).

**D12: Proposal states are forward-moving; reopening creates a new version**  
*Decision:* Proposal states move forward only (open → closed_consensus, closed_stall, or closed_consensus_creation_failed). When an organizer reopens a closed proposal, the system creates a new version with state = open. Old versions remain immutable for audit.  
*Rationale:* Immutable history for accountability and debugging. Clear lineage when people reopen proposals. No confusion about which deadline or slot set is active.  
*Implication:* Each proposal has a `version` field. Participants receive new invites for reopened versions. Old proposals can be archived after reopening.

**D13: Organizer dashboard displays full vote matrix with real-time auto-refresh and edit actions**  
*Decision:* Dashboard shows a complete vote matrix (responders × slots) with names, emails, and response status (responded/not). Auto-refreshes every 5 seconds. Organizer can add/remove slots, remove participants, extend deadline, and manually close proposals—all from the dashboard.  
*Rationale:* Full transparency enables quick decision-making. Real-time updates keep organizer informed without polling. Dashboard as command center reduces friction.  
*Implication:* Dashboard is information-rich and interactive. Requires WebSocket or polling for 5-second refresh cadence.

**D14: OAuth authentication for organizers; versioned participant links**  
*Decision:* Organizers authenticate via OAuth (Google, Microsoft). Participants click unique links (versioned per proposal version). Old links on closed/updated proposals show a message with a link to the latest version. Session timeout: 30 days of inactivity.  
*Rationale:* OAuth is familiar and secure. Versioned links prevent stale invites to closed proposals. Long session timeout is organizer-friendly.  
*Implication:* Organizer data tied to OAuth identity. Participants never log in—links are time-limited and proposal-specific.

**D15: Deadline is a hard cutoff for votes**  
*Decision:* The deadline is a hard cutoff. Votes received before the deadline are counted; votes at or after are rejected. At the deadline moment, the system checks for consensus. If met, proposal closes with consensus. If not, proposal closes with stall state.  
*Rationale:* Clear, predictable behavior. No grace periods or fuzzy boundaries. Organizers know exactly when decisions finalize.  
*Implication:* Participants receive a "Voting has closed" message if they try to vote after deadline. System must have accurate time synchronization for deadline checks.

**D16: Time slots include timezone; multi-timezone display with calendar auto-conversion**  
*Decision:* Organizers specify timezone when creating time slots. Slots display as "2:00 PM EST" to all participants. UI provides timezone conversion hover/click to see equivalent times in other timezones. Created Google Calendar events auto-convert to each participant's device timezone.  
*Rationale:* Clear primary reference (organizer's timezone) avoids ambiguity. Participants can easily check conversions. Google Calendar handles device-local display automatically.  
*Implication:* Slots stored with explicit timezone. UI needs timezone picker. Google Calendar event stores in organizer's timezone; participants' devices display locally.
