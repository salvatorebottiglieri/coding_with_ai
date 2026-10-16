# ADR 0014: OAuth Authentication for Organizers; Versioned Participant Links

## Status
Accepted

## Context
Who are organizers and how do they authenticate? Do participants log in? How are participant links managed across proposal versions?

- **Auth options:** Email/password (own system), OAuth (Google/Microsoft), SAML (enterprise).
- **Participants:** Full login, simplified login, or no login (just link).
- **Link versioning:** Same link forever, or version-specific links?

## Decision
- Organizers authenticate via OAuth (Google, Microsoft).
- Participants do not log in; they click version-specific links.
- Old links on closed/updated proposals show a message with a link to the latest version.
- Session timeout: 30 days of inactivity.

## Consequences
- **Positive:** OAuth is familiar and secure (no password management). No participant login friction. Versioned links prevent accidental voting on old versions.
- **Negative:** Depends on external OAuth providers. Participants can't access old proposal links directly. Organizer data is tied to OAuth identity.
- **Implementation:** OAuth callback → organizer session. Participant links are `https://app/vote/{proposal_id}/{version}/{token}`. System must track link versions and redirects.
- **Data:** Organizer email from OAuth becomes user ID. Session stored server-side with expiry.
- **UX:** Organizer login redirects to OAuth provider. Participants click link and go straight to voting (no login).
- **Security:** CSRF tokens on forms. Participant links are time-limited (e.g., expire 7 days after proposal closes).
