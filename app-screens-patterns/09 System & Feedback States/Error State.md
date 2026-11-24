# Error State

> Category: System & Feedback States

## Purpose
Network, server, or not-found failures with a retry action.

## Key Elements
- Icon matched to cause (offline cloud vs generic alert)
- Plain-language headline + one line of specifics
- Retry CTA; secondary path (go home, contact support)
- Error code/reference ID, small, for support

## States & Variations
- Offline (device has no connection) — distinct from server error
- Server 5xx / timeout; not-found (404); forbidden or expired session
- Partial failure: some modules loaded, one shows inline error
- Cached-content fallback with a stale banner

## Design Notes
- Never show raw exception strings; never blame the user
- Offline states should serve cached content where it exists — an app that goes fully blank offline feels broken
- Retry buttons must actually retry the failed thing, not reload the world

## Technical Considerations
- Build a typed error taxonomy at the network layer (Offline, Timeout, Server, NotFound, Unauthorized, Decode) mapped to UI states — string-matching error messages is unmaintainable
- Auto-retry transient failures with exponential backoff + jitter before showing UI at all
- Listen to reachability and auto-recover when the connection returns
- 401 → silent token refresh → replay request; only surface re-login if refresh fails. An error screen for an expired token is a bug
- Attach correlation/request IDs to errors, surface as the "error code," and log to crash/observability tooling

## References
- Offline-first patterns; Mobbin error-state collections
