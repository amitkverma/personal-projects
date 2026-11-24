# Empty State

> Category: System & Feedback States

## Purpose
Friendly placeholder when no data exists yet, with a CTA to start.

## Key Elements
- Illustration or icon (bundled, on-brand)
- Headline explaining what will live here
- One clear CTA to create/start/import
- Optional sample content or demo mode

## States & Variations
- First-use empty (educational, onboarding tone)
- Cleared/filtered empty ("no results for these filters" + reset)
- Post-deletion empty
- Each needs different copy — one generic empty state fits none of them

## Design Notes
- Never a dead end: always exactly one action
- First-use empties are onboarding real estate — teach the core loop here
- Filtered-empty must make the escape obvious (clear filters), or users think the app lost their data

## Technical Considerations
- Model three distinct states explicitly: not-yet-loaded, loaded-empty, and failed — conflating them causes the classic flash-of-empty-state bug while data is still loading
- Show empty only after the initial load/sync completes
- Bundle illustrations in the app; an empty state that needs the network to render is self-defeating
- Track empty-state impressions and CTA conversion — it measures onboarding effectiveness

## References
- Mobbin empty-state pattern collection
