# Home Dashboard

> Category: Core Navigation

## Purpose
Primary landing tab summarizing today's content, status, and quick actions.

## Key Elements
- Contextual header (greeting, date, current status)
- Hero module: the one thing to do now (today's task, primary metric)
- Quick-action row or chips
- Vertical feed of content/status cards
- Bottom tab bar (3–5 tabs)

## States & Variations
- Fresh install: starter content and setup nudges instead of emptiness
- Fully loaded / per-module skeletons while sections load independently
- Offline: render cached modules with a connectivity banner
- Module-level error: one failed section shows inline retry, rest stays alive

## Design Notes
- The first viewport must answer "what should I do right now?" — one primary action
- Modular card architecture lets you reorder/insert sections server-side without redesign
- Time-of-day personalization (morning vs evening content) is cheap and feels smart (see Headspace Today)

## Technical Considerations
- Server-driven layout (API returns an ordered module list) pays off quickly for iteration and A/B testing
- Cache per module with stale-while-revalidate: render cached instantly, refresh in background
- Isolate module failures — one endpoint's 500 must not blank the whole screen
- Prefetch dashboard data right after auth during launch, in parallel with the splash
- Pull-to-refresh triggers a coordinated refresh, not N independent spinners
- Track card impressions/taps with stable module IDs for ranking decisions

## References
- Headspace Today feed, Fi dashboard (Mobbin)
