# ADR 0010: Google Calendar Creation Failure Handling

## Status
Accepted

## Context
When consensus is reached, the system attempts to create a Google Calendar event. But Google Calendar API may be down, rate-limited, or encounter an auth error. Should the system:

- **Retry forever:** High reliability but organizer is left hanging, not knowing if event was created.
- **Retry N times, then fail:** Clear failure point, but event might not be created and organizer must act.
- **Retry N times, then revert consensus:** Go back to open state and let organizer retry later. But this violates the "consensus is final" principle.

## Decision
The system retries up to 3 times. If all retries fail, the proposal enters state `closed_consensus_creation_failed`. An email is sent **only to the organizer** with event details for manual creation. The proposal is locked and does not revert.

## Consequences
- **Positive:** Consensus is logically finalized (won't be undone). Organizer has all data to manually create event. Limits email spam to participants.
- **Negative:** Participants see "event created" in notification, but event may not exist in their calendar. Organizer must manually create and notify them if needed.
- **Implementation:** Need a separate proposal state. Email template must include all event details (title, time, timezone, attendees). Retry logic with exponential backoff.
- **UX:** Dashboard should show proposal state including `creation_failed`. Organizer sees a button to retry event creation or view manual creation instructions.
- **Future:** Consider async job queue (e.g., cron) to retry failed creations later.
