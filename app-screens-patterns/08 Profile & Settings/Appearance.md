# Appearance

> Category: Profile & Settings

## Purpose
Theme, language, and units preferences.

## Key Elements
- Theme: System / Light / Dark with live preview
- Text size (if not deferring to OS)
- Language selector; units (metric/imperial); date/time format
- Optional alternate app-icon picker

## States & Variations
- Following system vs explicit override
- Each change applied instantly, no restart
- Per-account (synced) vs per-device preferences

## Design Notes
- Default to "follow system" — overriding OS preferences by default annoys users
- Live preview beats descriptions
- Alternate icons are cheap delight for premium tiers

## Technical Considerations
- Theming works only with semantic design tokens (colorSurface, colorTextPrimary) — direct hex references make dark mode a repaint project; apply via overrideUserInterfaceStyle (iOS) / AppCompatDelegate night mode (Android)
- In-app language: iOS 13+ gives per-app language in Settings for free; a custom in-app switcher requires locale plumbing and immediate UI re-render — decide if it's worth it
- Units: store canonical (metric), convert at display; formatting via NumberFormatter/ICU respecting locale
- Persist server-side if preferences should roam across devices
- Alternate icons: pre-registered in the app bundle (iOS setAlternateIconName / Android activity-alias)

## References
- Platform dark-mode guides; Telegram appearance settings as a rich example
