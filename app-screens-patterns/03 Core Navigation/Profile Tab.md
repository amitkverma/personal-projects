# Profile Tab

> Category: Core Navigation

## Purpose
Entry point to the user's identity, stats, and settings.

## Key Elements
- Avatar, name, membership/premium badge
- Key stats row (streak, totals, milestones)
- Shortcut list: settings, help, saved/downloads
- Subscription status with manage/upgrade CTA

## States & Variations
- Logged-in vs guest (login/signup CTA replaces identity block)
- Free vs premium presentation
- Pending states: unverified email banner, sync in progress

## Design Notes
- This tab attracts every feature's leftovers — enforce hierarchy: identity → status → shortcuts, and push everything else into Settings
- Stats here should celebrate, not audit; deep analysis belongs in a Stats screen
- The upgrade CTA earns its place only for free users; hide it for subscribers

## Technical Considerations
- Cache the profile locally; refresh on tab focus, not on every render
- Subscription entitlement must come from server-side receipt validation — never trust client store state alone; this tab is where mismatches become visible
- Guest mode: define exactly which rows work without an account and gate the rest with a login sheet
- Avatar upload: crop/resize client-side, upload in background, show optimistic image immediately

## References
- Headspace profile tab (Mobbin)
