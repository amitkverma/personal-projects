# Profile View

> Category: Profile & Settings

## Purpose
Public or personal identity page with avatar, bio, and stats.

## Key Elements
- Avatar, display name, handle, joined date
- Stats row (followers, entries, streak — whatever the domain values)
- Bio/description
- Own profile: Edit button; others': Follow/Message/menu (report, block)
- Content tabs or shelves (posts, saved, activity)

## States & Variations
- Own vs other user's profile (different action sets, same layout)
- Private profile (limited view), blocked, suspended
- Incomplete profile with completion nudges

## Design Notes
- Design own-view and public-view as two explicit states of one layout — teams that don't end up leaking private data into public view
- The stats row should link to detail where meaningful
- Report/block must be reachable but not prominent

## Technical Considerations
- Privacy enforcement is server-side: the API returns only fields the viewer may see; the client never filters sensitive data itself
- Deep-linkable user routes (by handle and by ID; handles can change)
- Block/report take effect in local UI immediately (hide content) independent of network latency
- Avatar caching with cache-busting on change (versioned URL)
- Refresh-on-focus with cached render first

## References
- Instagram/X profile anatomy (Mobbin)
