# Consensus Calendar Event App

## Goal ✅

Build a comprehensive consensus-based calendar platform that enables users to create and schedule events across multiple calendar systems with participant consensus on timing. Events support single and recurring meetings, integrate with external calendars (Google, Outlook, iCal), and are accessible from web and mobile. Users can coordinate availability, auto-confirm or manually lock times, request reschedules, and add locations/video conferencing.

## Scope ✅

### Phase 1: Core MVP (Weeks 1-4)

**Single-day consensus scheduling:**

- Create single-day calendar events with immediate insertion into calendar
- Generate availability/time slot suggestions based on day hours (selectable granularity: hourly, 30-min, 15-min)
- Invite users or allow them to join existing events
- Track participant availability responses (real-time visibility to all participants)
- Auto-confirm at 24-hour deadline with best time slot, or allow organizer to manually confirm earlier
- Support both internal (team) and external (external groups) usage
- Send invite emails to participants immediately when event created
- Send confirmation/reminder emails to all participants when event time is confirmed (manually or auto)
- Send reschedule request notifications to organizer; send approval/rejection notifications to requester
- Web app only (desktop + tablet responsive)
- Single timezone per app instance (configurable)

### Phase 2: Extended Features (Weeks 5-10)

**Recurring events:**
- Support recurring patterns (daily, weekly, monthly, custom)
- Consensus voting for entire series or individual occurrences
- Edit/skip individual occurrences without affecting series

**External calendar integrations:**
- Google Calendar sync (two-way: read events, write confirmations)
- Outlook/Microsoft Calendar sync
- iCal feed import/export
- Show conflicts with external calendars during availability voting

**Multi-day and all-day events:**
- Support multi-day events (e.g., conference, retreat)
- All-day event handling
- Time slot suggestions span multiple days

**Location and video conferencing:**
- Location field with mapping integration
- Auto-generate Zoom/Teams/Meet links
- Send conference links in confirmation emails
- Participant can join directly from event details

### Phase 3: Mobile + Advanced (Weeks 11-14)

**Mobile app:**
- iOS app (native or React Native)
- Android app (native or React Native)
- Push notifications for invites, confirmations, reschedule decisions
- Offline event viewing

**Advanced features:**
- Event analytics and reporting
- Participant availability trends
- Admin dashboard for failed emails
- Bulk event creation and invitations

### Out of Scope (explicitly)

- Event analytics or reporting (Phase 3)
- More than one reschedule round per event (reschedule locks in; no further changes)

## Constraints ✅

- **Technical**: REST API backend; Phase 1 = web-based UI (React/Vue); Phase 3 = native/RN mobile; multi-calendar support via external integrations
- **Business**: Must support both internal team use and external group coordination; B2B SaaS model with per-org timezone settings
- **Time**: Phase 1 (4 weeks) = MVP with core consensus; Phase 2 (6 weeks) = recurring + integrations; Phase 3 (4 weeks) = mobile + analytics

## User Stories ✅

### Phase 1: Core Consensus

- As an **organizer**, I want to **create an event for a specific day** so that **it immediately appears in my calendar with time slot suggestions**.
- As an **organizer**, I want to **invite participants** so that **they can see the event and indicate their availability**.
- As a **participant**, I want to **receive an invite to an event** so that **I can view the proposed time and respond with my availability**.
- As a **participant**, I want to **indicate when I'm available** so that **the organizer can see my preferences and all others can see responses in real-time**.
- As an **organizer**, I want to **see all participant responses** so that **I can confirm the best time early or let it auto-confirm at 24 hours**.
- As a **participant**, I want to **receive confirmation** so that **I know the final locked-in meeting time**.
- As an **organizer or participant**, I want to **request a reschedule** so that **the event time can be changed if circumstances change post-confirmation**.
- As an **organizer**, I want to **review reschedule requests and approve/reject them** so that **I can maintain control over final scheduling decisions**.

### Phase 2: Recurring + Integrations

- As an **organizer**, I want to **create recurring events** so that **I can schedule repeating meetings with consensus on the entire series or individual occurrences**.
- As a **participant**, I want to **see conflicts from my Google Calendar during voting** so that **I can avoid availability conflicts**.
- As an **organizer**, I want to **add locations and video conference links** so that **participants know where/how to join**.
- As an **organizer**, I want to **sync confirmed events to my external calendar** so that **I don't have to manually create them elsewhere**.

### Phase 3: Mobile + Analytics

- As a **mobile user**, I want to **receive push notifications for event invites and confirmations** so that **I don't miss important updates**.
- As an **organizer**, I want to **see analytics on participant response times and availability patterns** so that **I can optimize future scheduling**.
- As an **admin**, I want to **view failed email logs and retry delivery** so that **no invite is lost due to delivery failures**.

## Acceptance Criteria ✅

### Phase 1: Core Consensus

- Event created by organizer is immediately visible in their calendar
- Availability time slots are suggested for the created date (granularity selectable: hourly, 30-min, 15-min)
- Invited participants can view the event, see all other responses in real-time, and respond with their availability
- **Invite email sent to all invited participants immediately when event created** (includes event title, proposed date, link to respond, deadline for consensus)
- Organizer dashboard shows all participant responses in a clear heatmap view
- Organizer can manually select a time slot and confirm it at any time
- Event auto-confirms at 24-hour deadline with the best time slot (highest availability; ties broken by earliest time chronologically)
- Once confirmed (manually or auto), all participants receive confirmation email with final locked-in time
- Participants not responding within 24 hours are still visible (pending status)
- **Post-confirmation: Any participant or organizer can request a reschedule**
- **Reschedule request includes: requester, reason (optional), proposed new time window**
- **Organizer receives reschedule request notification email and can approve/reject with reason**
- **If approved: event reverts to consensus phase with new date/time window; participants re-vote and receive reminder email**
- **If rejected: requester notified via email with rejection reason; event remains at confirmed time**
- **Only one reschedule round allowed per event (no further reschedules after second confirmation)**

### Phase 2: Recurring + Integrations

- Organizer can create recurring events (daily, weekly, monthly, custom patterns)
- Recurring event voting shows consensus for entire series or allows voting per occurrence
- System syncs confirmed events to connected Google Calendar / Outlook accounts
- Organizer can add location and select video conference provider (Zoom/Teams/Meet)
- Conference link auto-generated and sent in confirmation emails
- Participants' external calendar conflicts displayed during availability voting
- Multi-day events supported; time slots can span multiple days

### Phase 3: Mobile + Analytics

- Push notifications sent to mobile app for invites, confirmations, reschedule decisions
- Analytics dashboard shows response rates, peak availability times, participant patterns
- Admin can view failed email logs and trigger manual retry
- Offline event viewing available on mobile

## UI/Screens ✅

### Phase 1: Core Web App

1. **Event Creation Form** — Title, date picker, list of participants to invite/add, **granularity selector** (hourly, 30-min, 15-min)
2. **Calendar View** — Shows the created event placeholder with "pending consensus" badge
3. **Time Slot Grid** — Visual availability matrix (rows = participants, columns = hours/slots, cells = color-coded). **All participants can see each other's responses in real-time.**
4. **Participant Response Interface** — Simple click/drag to mark available time slots (respects selected granularity)
5. **Organizer Dashboard** — Shows all responses, heatmap of best times, "Confirm" button
6. **Event Confirmation Screen** — Final locked-in event details to share with all
7. **Reschedule Request Form** — For any participant/organizer to request reschedule (reason, proposed new date/time window)
8. **Organizer Reschedule Review** — Shows all pending reschedule requests with option to approve/reject + reason

### Phase 2: Extended Features UI

9. **Recurring Event Wizard** — Set recurrence pattern, voting scope (series or per-occurrence)
10. **External Calendar Settings** — Connect Google/Outlook accounts, manage sync preferences
11. **Event Details with Location** — Add location, select video conference provider, auto-generate link
12. **Conflict Checker** — Show external calendar conflicts during availability voting

### Phase 3: Mobile + Analytics

13. **Mobile App (iOS/Android)** — Responsive version of Screens 1-8, plus push notifications
14. **Analytics Dashboard** — Response rate trends, availability heatmaps, participant patterns
15. **Admin Email Log Dashboard** — Failed email queue, retry controls, delivery status

## Risks ✅

### Phase 1 Risks

#### Risk: Email Delivery Failures

- **Likelihood**: Medium
- **Impact**: High
- **Mitigation**: Implement email retry logic (exponential backoff, 3 retries). Log failures. Provide admin dashboard to view failed emails. In-app notifications as fallback for critical events (confirmation, reschedule decisions).

#### Risk: Timezone Handling

- **Likelihood**: High
- **Impact**: High
- **Mitigation**: For v1, use single timezone per app instance (configurable). Enforce consistent timezone display in all UIs. Include timezone in all email communications. Plan multi-timezone support for Phase 2.

#### Risk: Auto-Confirm Chooses Wrong Time

- **Likelihood**: Low
- **Impact**: Medium
- **Mitigation**: Organizer always has option to manually override before/at deadline. Clear heatmap visualization helps organizer spot conflicts before auto-confirm. Add "preview" before auto-confirm triggers.

#### Risk: Participant Fatigue

- **Likelihood**: Medium
- **Impact**: Low
- **Mitigation**: 24-hour window is aggressive but necessary for MVP. Track via analytics. Consider longer windows in future if adoption lags.

#### Risk: Reschedule Abuse (Endless Rescheduling)

- **Likelihood**: Medium
- **Impact**: Medium
- **Mitigation**: Hard limit: only one reschedule round allowed per event. After second confirmation, no more reschedules. Organizer decides whether to create new event if further changes needed.

#### Risk: Organizer Ignores Reschedule Requests

- **Likelihood**: Medium
- **Impact**: Low
- **Mitigation**: Add notification/reminder for pending reschedule requests. Set SLA (e.g., "organizer must decide within 24 hours"). Recommend UI badge showing pending reschedule count.

### Phase 2 Risks

#### Risk: External Calendar API Rate Limits & Failures

- **Likelihood**: High
- **Impact**: Medium
- **Mitigation**: Implement exponential backoff and queued sync jobs. Cache external calendars locally. Graceful degradation if sync fails (show cached data). Monitor API quota usage.

#### Risk: Recurring Event Scope Creep

- **Likelihood**: High
- **Impact**: High
- **Mitigation**: Define strict recurrence pattern limits (daily, weekly, monthly, custom). No timezone-aware recurrence in Phase 2. Limit to 52 occurrences per series. Defer complex patterns to Phase 3.

#### Risk: Video Conference API Integration Issues

- **Likelihood**: Medium
- **Impact**: Medium
- **Mitigation**: Use simple URL-based links for Zoom/Teams (no auth required initially). Add SSO integration later. Test all providers before launch.

### Phase 3 Risks

#### Risk: Mobile Push Notification Delivery

- **Likelihood**: Medium
- **Impact**: High
- **Mitigation**: Use battle-tested service (Firebase Cloud Messaging). Implement fallback to in-app notifications. Monitor delivery rates and adjust strategy based on metrics.

#### Risk: Analytics Performance Degradation

- **Likelihood**: Medium
- **Impact**: Medium
- **Mitigation**: Implement denormalized analytics tables (separate from transactional DB). Use read replicas for reporting queries. Pre-aggregate data nightly if needed.

#### Risk: Mobile App Store Review Delays

- **Likelihood**: High
- **Impact**: Low
- **Mitigation**: Start review process early. Ensure compliance with store policies. Provide clear legal/privacy docs. Plan for 1-2 week review cycles.