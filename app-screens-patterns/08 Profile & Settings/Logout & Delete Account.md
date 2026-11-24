# Logout & Delete Account

> Category: Profile & Settings

## Purpose
Sign-out and destructive account-removal confirmations.

## Key Elements
- Logout with lightweight confirm
- Delete flow: consequence explainer (what's lost, what's retained and for how long) → re-auth challenge → final confirmation (typed word or hold-to-confirm) → farewell state
- Alternatives offered once: pause/deactivate, export data first

## States & Variations
- Logout confirm
- Deletion pending (grace period, with cancel-deletion path)
- Deleted (signed out, local data wiped)
- Blocked: active subscription warning first

## Design Notes
- Logout should be easy; deletion deliberate but not obstructed — endless retention dark patterns violate store policy and user trust
- Explain subscription implications explicitly (deleting the account does NOT cancel an App Store subscription — tell them how)
- Offer export before delete, once

## Technical Considerations
- Logout checklist: revoke tokens server-side; clear Keychain/Keystore, local DB, caches, files; unregister push token; reset in-memory state — partial logout causes ghost-data bugs across accounts
- Apple requires in-app account deletion if the app has account creation; Play has equivalent policy
- Deletion as an async server job: re-auth gate → grace window (e.g. 30 days, cancellable) → cascade or anonymize per retention policy, including third-party processors
- Send deletion confirmation email; keep a minimal legal tombstone record if required
- Test the "delete then re-register same email" path — it breaks surprisingly often

## References
- Apple account-deletion requirement docs; GDPR erasure guidance
