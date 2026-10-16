# ADR 0016: Time Slots Include Timezone; Multi-Timezone Display

## Status
Accepted

## Context
Participants may be in different timezones. When an organizer proposes "2:00 PM Tuesday," in which timezone? How should participants see it?

- **Organizer timezone only:** Simple, but participants must manually convert.
- **Multiple timezones displayed:** Shows 2 PM EST = 7 PM GMT. Complex but helpful.
- **Auto-detect participant timezone:** Calendar link converts to each person's local time. Simplest for participants but hides organizer's intent.

## Decision
Organizers specify timezone when creating time slots. Slots display as "2:00 PM EST" to all participants. UI provides timezone conversion (hover/click to see equivalent times in other timezones). Google Calendar events auto-convert to each participant's device timezone.

## Consequences
- **Positive:** Clear, single source of truth (organizer's timezone). Participants can easily check conversions. Google Calendar handles device-local display. No hidden timezone surprises.
- **Negative:** Participants must be aware of timezone. UI must support timezone picker and conversion logic. Multiple timezones in display add visual complexity.
- **Implementation:** Slots stored with `time`, `date`, and `timezone_id` (IANA tz database). Consensus checks operate on UTC equivalents. UI renders with conversion helper. Google Calendar event created in organizer's timezone; clients display locally.
- **Data:** Proposal stores organizer's timezone. Each slot has its own timezone (all typically same, but could vary).
- **UX:** Timezone picker when creating/editing slots. Timezone converter widget on voting page. Google Calendar event details show "Converted to your timezone: ..."
