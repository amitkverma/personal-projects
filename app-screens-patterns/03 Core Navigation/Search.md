# Search

> Category: Core Navigation

## Purpose
Query input with suggestions, results list, and filters; includes empty and no-results states.

## Key Elements
- Search field with clear (×) and cancel
- Pre-query state: recent searches + trending/suggested terms
- Typeahead suggestions while typing
- Results list with thumbnail, title, metadata; filter/sort controls

## States & Variations
- Empty (pre-query) / suggesting / loading / results
- No results — with spelling suggestions or category alternatives
- Error with retry
- Filtered results with active-filter chips

## Design Notes
- Show recents instantly on focus; it's the fastest path for repeat searches
- No-results must offer a way forward (broaden, browse categories), never a dead end
- Highlight the matched term in results

## Technical Considerations
- Debounce input ~250–300ms AND cancel in-flight requests — otherwise a slow early response overwrites a fast later one (stale-response race)
- Use a real search backend (Algolia/Elasticsearch/Typesense) for typo tolerance, synonyms, and ranking; client-side filtering only works for tiny datasets
- Log all queries and especially zero-result queries — they are a product roadmap
- Store recents locally with a cap; offer per-item delete for privacy
- Paginate results; keyboard: submit-on-return, dismiss-on-scroll
- Voice input is mostly free via the keyboard — don't build custom unless core

## References
- Headspace search results list (Mobbin)
