# Success Celebration

> Category: System & Feedback States

## Purpose
Positive reinforcement after completing a key action.

## Key Elements
- Success mark, confetti, or character animation + haptic
- Headline naming the achievement
- Earned-thing summary: streak count, stat, badge
- Next-step CTA; optional share

## States & Variations
- First-time achievement (big) vs routine completion (small)
- Milestone tiers (7-day, 30-day, 100-day)
- Inline toast-level success vs full-screen moment

## Design Notes
- Match intensity to the achievement — confetti for a daily log reads as desperate by day three
- Never block the next action behind an animation; celebration is a garnish, not a gate
- The post-success moment is the right time for review prompts and referral hooks (see Headspace's session-complete screen)

## Technical Considerations
- Pair animation with haptics (UINotificationFeedbackGenerator success / Android HapticFeedback)
- Lottie for rich animations — audit added bundle size and rasterization cost on low-end devices
- Make animations interruptible; user taps skip everything instantly
- Respect prefers-reduced-motion: swap animation for a static state
- Fire the conversion analytics event here exactly once
- Milestone logic server-side if streaks/badges matter (client clocks can't be trusted)

## References
- Duolingo streak celebrations; Headspace "Minutes Meditated" completion (Mobbin)
