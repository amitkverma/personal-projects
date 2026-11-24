# Toasts & Banners

> Category: System & Feedback States

## Purpose
Transient inline feedback for background events.

## Key Elements
- Toast/snackbar: bottom-anchored, auto-dismissing, message + optional single action (Undo, View)
- Banner: top-anchored, persistent while a condition holds (offline, sync paused, trial ending)
- Distinct styling per severity (neutral, success, warning)

## States & Variations
- Queued toasts (sequential display)
- Toast with action tapped vs auto-dismissed
- Persistent banner appearing/resolving with app state
- Stacked conditions (offline + trial-ending) needing priority rules

## Design Notes
- Toasts for confirmations of what just happened; banners for ongoing conditions — don't swap the roles
- One toast at a time; queues beat overlaps
- Critical information never lives only in a toast — it disappears; anything requiring action needs a persistent surface

## Technical Considerations
- One global toast manager rendering in a root overlay — per-screen implementations cause overlap chaos and dismissal bugs during navigation
- Accessibility: announce via VoiceOver/TalkBack live regions; auto-dismiss timers must meet minimum readable durations and pause on interaction
- The Undo pattern: delay the real commit (or use server-side soft-delete) until the toast window expires — undo that "un-sends" an already-committed action is a lie that eventually breaks
- Banners bind to observable state (connectivity monitor, sync engine status) and resolve themselves
- Define a severity/priority enum so simultaneous banners have a deterministic winner

## References
- Material Snackbar spec; offline-banner patterns (Mobbin)
