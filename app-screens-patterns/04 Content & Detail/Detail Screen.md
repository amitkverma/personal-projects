# Detail Screen

> Category: Content & Detail

## Purpose
Full view of a single item (product, article, course, event) with primary CTA.

## Key Elements
- Hero media (image/illustration/video)
- Title + metadata row (type, duration, rating, author)
- Description with expand/collapse for long text
- Primary CTA — prominent or sticky (Play, Book, Buy, Start)
- Secondary actions: save/favorite, share
- Related-items rail

## States & Variations
- Skeleton or hero-first progressive load
- Content unavailable (deleted, region-locked, expired)
- Offline with cached data
- Owned/started vs new (CTA text changes: "Continue" vs "Start")

## Design Notes
- The primary CTA must be visible without scrolling — sticky bottom bars solve long content
- Secondary actions as icons near the title (see Headspace course detail: heart + share)
- Related content at the bottom drives session depth more than anything else on the screen

## Technical Considerations
- Deep-linkable by ID as a first-class route; handle not-found/no-permission with a real screen, not a crash or blank
- Two-phase render: pass the lightweight list-item data forward for instant paint, fetch the full record in the background
- Shared-element transitions from list to detail are high polish-per-effort
- Share via universal links/app links so recipients open the app (or a web fallback)
- Cache detail payloads keyed by ID with sensible TTL

## References
- Headspace course detail with teacher picker (Mobbin)
