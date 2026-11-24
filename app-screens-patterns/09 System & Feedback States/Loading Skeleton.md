# Loading Skeleton

> Category: System & Feedback States

## Purpose
Placeholder shimmer layout shown while content loads.

## Key Elements
- Grey shapes mirroring the final layout (avatar circle, text bars, image blocks)
- Subtle shimmer/pulse animation
- Per-module skeletons for independently loading sections

## States & Variations
- Full-screen first load vs per-module refresh
- Paging skeleton at list bottom
- Timeout → hands off to error state

## Design Notes
- The skeleton must match the real layout closely; a mismatched swap is worse than a spinner
- Use skeletons for expected waits >300ms; brief in-place waits do better with nothing or a tiny spinner
- Don't shimmer forever — anything past a few seconds needs a message

## Technical Considerations
- Build the skeleton as a variant of the real component (same layout code, placeholder styling) so the two can't drift apart
- Animate with GPU-cheap properties (opacity/gradient transform), not layout
- Always pair with a timeout that transitions to the error state — an infinite skeleton is an outage you can't see
- Reserve final content dimensions (image aspect ratios) to prevent layout shift on arrival
- Respect reduced-motion accessibility settings (static placeholders instead of shimmer)

## References
- Facebook's original shimmer pattern; Mobbin loading collections
