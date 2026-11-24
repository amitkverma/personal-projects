# Activity History

> Category: Core Navigation

## Purpose
Chronological log of the user's past actions, entries, or sessions.

## Key Elements
- List grouped by day (Today, Yesterday, then dates)
- Per-row: type icon, title, time, key value (duration/amount)
- Per-day summary totals
- Type filter chips; row swipe actions (edit/delete)

## States & Variations
- Empty (no activity yet) with a log-first CTA
- Loading more (infinite scroll) / end of history
- Filter applied with zero matches
- Pending-sync rows (logged offline, not yet uploaded)

## Design Notes
- Natural time buckets beat raw timestamps; per-group totals give the list meaning
- Rows should open a detail/edit view; history that can't be corrected frustrates
- Show sync status subtly (small icon), not loudly

## Technical Considerations
- Cursor-based pagination, not offset — new items inserted at the top shift offsets and cause duplicates/gaps
- Local-first storage (SQLite/Room/Core Data/GRDB) with background sync gives instant load and offline logging for free
- Day grouping must use the user's current timezone; be explicit about UTC-boundary behavior when the user travels
- Swipe-to-delete: optimistic UI with an undo toast; commit the server delete after the undo window
- Emit list diffs (DiffUtil/snapshot diffing) so inserts/edits animate instead of reloading

## References
- timespent session list, Google Fit journal (Mobbin)
