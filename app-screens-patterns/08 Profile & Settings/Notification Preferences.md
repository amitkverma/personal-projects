# Notification Preferences

> Category: Profile & Settings

## Purpose
Per-channel and per-topic notification toggles.

## Key Elements
- Master toggle
- Category toggles in user language (Reminders, Activity, Tips, Marketing)
- Per-channel controls (push/email/SMS) where applicable
- Quiet hours; OS-permission fix banner when denied at system level

## States & Variations
- OS permission denied: toggles moot — banner deep-links to system settings
- Mixed per-category states; marketing consent captured separately
- Channel-specific rows (email digest frequency)

## Design Notes
- Name categories by user benefit ("Reminders to log"), never internal jargon ("transactional")
- Master-off should visually disable (not hide) the rest
- Marketing defaults must follow regional law (opt-in in much of the world)

## Technical Considerations
- Preferences live server-side — the sending system enforces them; the app is just the editor. Cache locally for instant render
- Two gates must both pass: OS-level permission AND user preference; reconcile on every foreground
- Model as topic subscriptions in your push infrastructure (FCM topics or a routing table in your notification service)
- Changes take effect immediately — invalidate any queued sends on the server side
- Keep a consent audit trail (what, when, from where) for GDPR/TCPA marketing compliance
- Quiet hours are evaluated in the user's timezone by the sender

## References
- Headspace mindful-moments toggles (Mobbin)
