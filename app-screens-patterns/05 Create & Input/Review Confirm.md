# Review Confirm

> Category: Create & Input

## Purpose
Read-back of entered data before final submission.

## Key Elements
- Read-only summary grouped into labeled sections
- Edit link per section that jumps back to the right step
- Total/impact line (cost, duration, what will happen)
- Final CTA with unambiguous verb; legal fine print if applicable

## States & Variations
- Reviewing / round-tripped back from an edit
- Submitting (CTA locked against double-tap)
- Failure with errors mapped to their sections
- Post-submit receipt view

## Design Notes
- This is the trust screen: no new information, no surprise fees, nothing unexplained
- Edit-in-place round-trips beat restarting the flow
- CTA copy states the action and its weight: "Place order — $42.18", not "Continue"

## Technical Considerations
- Render the summary from the exact state object that will be submitted — any drift between what is shown and what is sent is a bug factory
- Double-submit protection at both ends: disable the CTA on tap AND enforce an idempotency key server-side
- Map server validation errors back to sections with scroll-to-error
- Sticky CTA over a scrollable summary; the button must never be pushed off-screen
- Log a review-viewed event; the review→submit conversion rate flags trust problems

## References
- Checkout review steps (Amazon, Stripe-based flows)
