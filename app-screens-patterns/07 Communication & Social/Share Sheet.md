# Share Sheet

> Category: Communication & Social

## Purpose
Export surface for sending content outside the app.

## Key Elements
- System share sheet (UIActivityViewController / Android chooser)
- Optional custom quick-row first: Copy link, WhatsApp, Instagram Stories
- Generated share asset: branded card image or rich link preview
- Success/cancel handling (usually silent)

## States & Variations
- Sharing a link vs an image vs a composed card
- Generating-asset spinner (keep it sub-second)
- Target-specific composition (Stories background + sticker vs plain URL)

## Design Notes
- Share content, not screenshots of UI chrome — a designed share card represents the brand in other people's feeds
- Copy-link deserves first position; it's the most-used action almost everywhere
- Never block sharing on a network call; degrade to the plain link

## Technical Considerations
- Universal links / app links with server-rendered OG meta tags give rich previews in messengers and route recipients into the app (with web fallback)
- Generate share images off the main thread; cache per content ID
- Instagram Stories and some targets need their specific pasteboard/intent APIs, not the generic sheet
- Append source/UTM parameters per share target for attribution
- The receive side is half the feature: a deep-link router that handles logged-out users, missing content, and old link formats

## References
- Spotify share cards, Headspace guest-pass share (Mobbin)
