# Rate the App

> Category: Engagement & Growth

## Purpose
Prompt asking satisfied users for a store review.

## Key Elements
- Pre-prompt sentiment gate: "Enjoying the app?" Yes / Not really
- Happy path → OS in-app review dialog
- Unhappy path → in-app feedback form routed to support
- Dismiss without penalty

## States & Variations
- Never asked / deferred ("maybe later") / rated / gave feedback
- Cooldown after dismissal or a recent crash
- Store-specific dialogs (App Store vs Play)

## Design Notes
- Ask after a success moment (completed session, milestone) — never at launch, never after an error
- The sentiment gate routes unhappy users to support instead of the store; this is standard practice, but keep the unhappy path genuinely useful, not a review-deflection trap
- Don't beg, don't offer rewards for ratings (policy violation)

## Technical Considerations
- SKStoreReviewController.requestReview (iOS) / Google Play In-App Review API — the OS decides whether the dialog actually appears and caps frequency (iOS ~3 prompts/365 days), so your trigger must tolerate silent no-ops
- You cannot detect whether the dialog showed or what rating was given — design analytics around trigger events, not outcomes
- Build an eligibility engine: minimum sessions/days installed + success event just occurred + no recent crash + cooldown elapsed; persist its state
- Keep triggers server-configurable to tune without releases
- Deep link "write a review" in settings to the store review page for users who seek it out voluntarily

## References
- Apple/Google in-app review API docs and policies
