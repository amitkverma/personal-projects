# Notifications Inbox

> Category: Communication & Social

## Purpose
In-app list of alerts, updates, and activity mentions.

## Key Elements
- Rows: avatar/type icon, message, relative timestamp, unread dot
- Grouping by recency (New / Earlier) or by type tabs
- Mark-all-read; swipe actions (dismiss, mute type)
- Shortcut to notification preferences; empty state

## States & Variations
- Mixed unread/read / all read / empty
- Aggregated rows ("Maya and 3 others liked your post")
- Action-required rows with inline buttons (accept/decline)
- Loading more (pagination)

## Design Notes
- Every row must deep-link to something useful; a notification that lands nowhere trains users to ignore the inbox
- Aggregate similar events aggressively — 40 individual like-rows is noise
- One tap from any row to muting that notification type builds trust

## Technical Considerations
- Separate the two systems: push notification (transport, ephemeral) vs inbox record (state, persistent). The inbox is its own API, not a log of pushes
- Read-state must sync across devices; server-authoritative unread count drives the tab badge and app icon badge
- Batch mark-as-read calls; don't fire one request per row scroll-past
- Define retention/TTL for old items server-side
- Deep-link routing table shared with push handling — one resolver for both entry points
- Cursor pagination; new items arrive via push or on-focus refresh

## References
- Instagram/LinkedIn activity feeds (Mobbin)
