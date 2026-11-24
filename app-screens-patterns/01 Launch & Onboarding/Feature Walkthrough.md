# Feature Walkthrough

> Category: Launch & Onboarding

## Purpose
Coach marks or tutorial overlays that highlight key UI on first use.

## Key Elements
- Dimmed overlay with a spotlight/cutout on the target element
- Tooltip: short instruction + Next/Done
- Step counter when multi-step
- Obvious dismiss (tap outside or X)

## States & Variations
- First-launch tour vs feature-release tour for existing users
- Inline tutorial cards embedded in the layout (less intrusive alternative)
- Interactive "do it to advance" steps vs passive "read and next"
- Re-triggerable from a Help menu

## Design Notes
- Three steps maximum — completion drops sharply beyond that
- Teaching by doing (guide the real first action) beats describing UI
- Never block a critical action behind a tour; everything must be skippable
- Prefer progressive disclosure (tooltips appearing on first encounter) over one big tour

## Technical Considerations
- Anchoring tooltips to live view coordinates is fragile: recompute on layout changes, test small screens, landscape, and font scaling
- Wait for the first layout pass before presenting — anchors are wrong on first frame
- Persist per-feature "seen" flags, keyed and versioned, so future features can add their own walkthroughs independently
- Accessibility: overlays confuse screen readers — either manage VoiceOver/TalkBack focus explicitly or skip the tour when a screen reader is active
- Keep walkthrough definitions declarative (target id, text, order) so they're data, not scattered code

## References
- Material Design onboarding guidance
- Coach-marks pattern (Mobbin UI-element category)
