# Force Update

> Category: System & Feedback States

## Purpose
Blocking screen requiring an app upgrade or announcing maintenance.

## Key Elements
- Full-screen takeover, friendly illustration
- Explanation of why (benefit-framed when possible)
- Update CTA deep-linking to the store listing
- Soft variant: "Remind me later" dismissal

## States & Variations
- Soft nudge (dismissible, shown periodically)
- Hard block (version below minimum supported)
- Maintenance mode (server-side outage, time-boxed message)
- Store-unavailable fallback (web link)

## Design Notes
- Soft-nudge early and often; hard-block rarely and apologetically
- Explain the benefit ("this version can't sync new entries") rather than issuing demands
- Maintenance screens should state an expected end time if known

## Technical Considerations
- Ship the version-gate mechanism in v1.0 — you cannot retrofit a kill switch onto clients that never check
- Gate via remote config/API returning min_supported_version and latest_version; check at launch and on foreground
- Compare semantic versions correctly (2.10.0 > 2.9.0 — string comparison fails)
- The config endpoint must be unauthenticated, aggressively cached, and highly available; if it's down, fail open (let users in)
- Store deep links (itms-apps://, market://details?id=) with https fallbacks
- Keep maintenance mode a separate flag from update-required — different message, different resolution

## References
- Firebase Remote Config force-update recipes
