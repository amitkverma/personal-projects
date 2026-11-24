# Notification Opt-in Primer

> Category: Engagement & Growth

## Purpose
Persuasive pitch shown before the system notification prompt.

## Key Elements
- Illustration, often a mock of an actual notification
- Concrete benefit copy ("We'll remind you at feeding time")
- Primary CTA (Enable) that triggers the OS prompt
- "Maybe later" with honest visual weight

## States & Variations
- Pre-prompt / accepted → OS prompt / soft-declined (re-eligible later)
- OS-denied → future prompts become a settings deep-link banner
- Contextual variants: different pitch after different user actions

## Design Notes
- Show the actual notification they'll receive — a rendered example converts better than any abstract promise
- Time it just after the user does the thing notifications amplify (set a reminder, complete a session)
- Respect "maybe later" — re-ask on a new success moment, capped, not on a timer loop

## Technical Considerations
- iOS gives one real OS prompt ever — only fire it after primer acceptance; a soft-decline costs nothing and preserves the option
- Android 13+ POST_NOTIFICATIONS follows the same primer-then-request pattern; handle "denied twice = permanent" semantics
- iOS provisional authorization (quiet delivery, no prompt) is a legitimate middle path to demonstrate value first
- Persist primer history (shown count, declined at, context) to drive re-prompt eligibility rules
- Measure primer→OS-prompt→granted as a funnel; the primer's whole job is that conversion rate
- After grant, send a first notification promptly that proves the promised value

## References
- Headspace reminder primer (Mobbin); push-permission UX studies
