# Welcome Carousel

> Category: Launch & Onboarding

## Purpose
Swipeable value-proposition slides introducing what the app does before sign-up.

## Key Elements
- 2–4 slides: illustration/photo, headline, one-line subtext each
- Page indicator dots
- Persistent primary CTA (Get Started / Continue) and a "Log in" link for returning users
- Skip affordance

## States & Variations
- First / middle / last slide (CTA often changes on the last)
- Auto-advancing vs user-driven paging
- Returning user: skipped entirely via a persisted flag
- Video or animated background variant

## Design Notes
- Sell outcomes ("sleep better"), not features ("18-session program")
- Keep copy to two lines max per slide; the image should carry the message
- The login link must be visible on slide one — returning users won't hunt for it
- Both swiping and the button must advance; users are split on which they use

## Technical Considerations
- Implement with the platform pager (UIPageViewController / SwiftUI TabView page style, ViewPager2 / Compose HorizontalPager)
- Persist a "has seen onboarding" flag; decide deliberately whether it is per-device or per-account (reinstall behavior differs)
- Preload slide images so paging never shows a blank frame
- Drive slide content/count from remote config to allow A/B testing copy without releases
- Fire an analytics event per slide view to find drop-off points
- Respect reduced-motion settings if slides animate

## References
- Headspace welcome + "science-backed" slides (Mobbin)
- Duolingo, Flo onboarding intros
