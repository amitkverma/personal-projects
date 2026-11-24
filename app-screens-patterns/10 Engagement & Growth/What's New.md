# What's New

> Category: Engagement & Growth

## Purpose
Changelog highlights shown after an update.

## Key Elements
- Version headline or release name
- 2–4 feature cards: small illustration, title, one-line benefit
- "Try it" deep link per feature where possible
- Continue/dismiss

## States & Variations
- Shown once per qualifying release
- Deep-linked into a highlighted feature
- Skipped for minor releases (bugfix-only versions shouldn't interrupt)

## Design Notes
- Reserve the sheet for genuinely user-visible changes; interrupting for "performance improvements" spends trust
- One screen maximum — a paged changelog is a skip-fest
- "Show, then let them do": the deep link into the new feature is worth more than the description

## Technical Considerations
- Gate on persisted last-seen-version vs current version; suppress entirely on first install (everything is new)
- Source content from remote config so a release's sheet can be edited, targeted, or killed after shipping
- Feature deep links must handle the flag-off case (feature rolled out to 10%) — never advertise what the user can't reach
- Compare versions semantically and support "minimum interesting version" so bugfix releases skip the sheet
- Localize the content; this is a marketing surface
- Track view/dismiss/feature-tap to learn whether the sheet earns its interruption

## References
- Slack and Figma release notes sheets; App Store "What's New" conventions
