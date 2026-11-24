# Settings Hub

> Category: Profile & Settings

## Purpose
Sectioned list linking to all configuration areas.

## Key Elements
- Grouped rows with icon, label, current-value hint, chevron
- Groups: Account, Notifications, Privacy, Appearance, Support, About
- Sign out (separated); version/build footer

## States & Variations
- Attention badges on rows (verify email, payment failing)
- Feature-flagged rows appearing per user/plan
- Search within settings (only for very large apps)

## Design Notes
- Order groups by frequency of use, not alphabetically
- Show the current value in the row ("Appearance — Dark") to save a tap
- Destructive/exit actions last and visually separated

## Technical Considerations
- Drive rows from a declarative config (id, icon, title, route, flag) — makes feature-flagging, A/B tests, and reordering trivial
- Every row should be deep-linkable so support docs can link directly to a setting
- Local settings (theme) vs server settings (notifications) need different persistence paths behind one facade
- Version/build/device-ID in the footer, tappable-to-copy — support teams will thank you
- Hidden developer menu (multi-tap on version) must be compiled out or auth-gated in release builds

## References
- iOS Settings, Headspace settings (Mobbin)
