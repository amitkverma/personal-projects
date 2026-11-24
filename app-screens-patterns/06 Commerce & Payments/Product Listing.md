# Product Listing

> Category: Commerce & Payments

## Purpose
Grid or list of purchasable items with price and filters.

## Key Elements
- Product cards: image, title, price, rating, badges (sale/new)
- Filter button with active-count badge; sort control
- Category header/breadcrumb
- Wishlist toggle per card

## States & Variations
- Skeleton grid on load / loaded / paging
- Filtered with zero results (show reset-filters CTA)
- Out-of-stock items (dimmed or "notify me")
- Grid vs list density toggle

## Design Notes
- Image consistency (uniform ratio, background) makes or breaks the grid
- Show applied filters as removable chips above results
- Sale pricing needs both prices (was/now) — a lone discounted price loses the anchor

## Technical Considerations
- Faceted search backend (filters and counts computed server-side); client-side filtering collapses beyond trivial catalogs
- Encode filter/sort state in the route or query params — shareable, restorable after process death
- Paginated grid with image prefetch for the next page
- Price and stock need short cache TTLs; showing stale prices creates support tickets and legal exposure
- Wishlist toggles: optimistic update with rollback on failure
- Standard ecommerce analytics events (view_item_list, select_item) with position data

## References
- Amazon, ASOS, Walmart listing patterns (Mobbin)
