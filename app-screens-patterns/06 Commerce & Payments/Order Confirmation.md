# Order Confirmation

> Category: Commerce & Payments

## Purpose
Success screen with order number and next steps.

## Key Elements
- Clear success mark + headline
- Order number (tappable to copy) and summary
- Delivery estimate and address recap
- Track-order / view-order CTA; continue-shopping secondary
- Optional referral/share hook

## States & Variations
- Fully confirmed vs payment-pending (bank transfers, async methods)
- Partially fulfilled orders
- Digital goods: immediate access CTA instead of delivery info

## Design Notes
- Celebrate briefly, then be useful: what happens next, when, and where to check
- Post-purchase is peak goodwill — the right moment for a review prompt or referral offer (one, not both)
- Email confirmation notice reassures; state it explicitly

## Technical Considerations
- The screen must be idempotent and re-openable: keyed by order ID, safe across refresh/reopen/deep link from email
- Confirmation email/push triggered by backend order events, never by the client reaching this screen
- Clear the cart only on a confirmed order event — not optimistically on CTA tap
- Fire the purchase analytics event exactly once (dedupe by order ID); it drives revenue reporting and ad attribution
- Handle the async-payment case honestly: "pending" state with what to expect

## References
- Standard ecommerce confirmations (Mobbin: order success patterns)
