# List Feed

> Category: Content & Detail

## Purpose
Scrolling collection of cards or rows, often infinite and personalized.

## Key Elements
- Cards/rows: thumbnail, title, metadata line, optional action (save, menu)
- Pull-to-refresh
- Pagination loader at the bottom
- Optional pinned/featured items at the top

## States & Variations
- First load (skeletons) / loaded / refreshing / paging
- Empty feed / end-of-feed marker
- Error with retry (full-screen if nothing cached, inline banner if cached content exists)
- New-content indicator ("new posts" pill) for live feeds

## Design Notes
- Standardize card anatomy; more than two card sizes in one feed reads as chaos
- Tap targets ≥44pt; whole card tappable, secondary actions clearly separated
- Preserve scroll position religiously — losing it is the fastest way to feel broken

## Technical Considerations
- Use list virtualization (RecyclerView / LazyColumn / UICollectionView / SwiftUI List) with stable item IDs and diff-based updates — full reloads cause flicker and lost positions
- Image loading via a real library (Coil/Glide/Kingfisher/SDWebImage): placeholders, request cancellation on recycle, memory + disk cache
- Cursor pagination with a prefetch threshold (start loading ~10 items before the end)
- Restore scroll position across back-navigation and process death
- Impression analytics need a visibility threshold (e.g. 50% visible for 1s), not raw cell-binding events
- Test with slow network + huge datasets; jank here defines perceived app quality

## References
- Headspace Today feed (Mobbin); Instagram/Twitter as canonical infinite feeds
