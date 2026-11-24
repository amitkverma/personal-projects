# Cart

> Category: Commerce & Payments

## Purpose
Editable summary of selected items with totals and promo codes.

## Key Elements
- Line items: image, title, variant, unit price, quantity stepper, remove
- Promo-code field with apply
- Cost breakdown: subtotal, shipping, tax, discount, total
- Checkout CTA; save-for-later section

## States & Variations
- Empty cart (browse CTA + saved items)
- Item went out of stock or price changed since adding — flagged inline
- Promo applied / invalid / expired
- Totals recalculating; merged cart after login

## Design Notes
- All edits inline; a separate edit screen per line is friction
- Surface stock/price changes here, before checkout — surprises at payment kill trust
- Show the full total as early as honesty allows; hidden costs at the last step are the top abandonment cause

## Technical Considerations
- Server-side cart as source of truth (cross-device sync, price integrity), with optimistic local updates for responsiveness
- All money math happens server-side; the client displays what the server computed — never sums floats locally as the displayed truth
- Debounce quantity-stepper mutations; coalesce rapid taps into one API call
- Promo validation server-side with specific failure reasons (expired vs minimum not met vs not applicable)
- Merge guest cart into account cart on login with a defined conflict rule
- Cart state feeds abandonment recovery (push/email) — track add/remove events

## References
- Amazon, Shopify-standard carts (Mobbin)
