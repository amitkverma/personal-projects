# Explore Browse

> Category: Core Navigation

## Purpose
Category-driven discovery surface for the app's full catalog.

## Key Elements
- Search entry point at the top
- Category chips or tile grid (Meditate / Sleep / Move style)
- Featured/editorial banner
- Horizontal content rails per collection with "see all"

## States & Variations
- Cold start (no personalization) vs personalized ordering
- Rail-level loading skeletons
- Empty category (rare but must not dead-end)
- Seasonal/campaign takeover banner

## Design Notes
- Blend editorial curation with algorithmic rails — pure algorithms get monotonous, pure editorial doesn't scale
- Keep the category taxonomy shallow (two levels max); deep trees die on mobile
- Every rail needs a "see all" destination; users treat rails as previews

## Technical Considerations
- Catalog served from a CMS or server-driven layout API with ETag/cache headers
- Image-heavy: serve CDN-resized variants per slot size, lazy-load offscreen rails
- Nested horizontal lists inside a vertical scroll are a classic jank source — recycle cells properly and cap rail item counts
- Make every category, collection, and banner deep-linkable for marketing campaigns
- Log rail impressions with position so ranking can be evaluated

## References
- Headspace Explore tab (Mobbin) — chips + guided program cards
