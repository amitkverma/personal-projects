# Orders & Billing History

> Category: Commerce & Payments

## Purpose
Past orders, subscriptions, invoices, and payment methods.

## Key Elements
- Order list: thumbnail, date, total, status chip
- Order detail: items, status timeline, invoice download, reorder
- Subscription block: plan, price, renewal date, manage/cancel
- Saved payment methods with default marker

## States & Variations
- Empty (no orders yet)
- In-progress statuses: processing, shipped, delivered, return/refund pending
- Failed renewal payment → dunning banner with fix-payment CTA
- Subscription in grace period or cancelled-but-active-until date

## Design Notes
- A status timeline communicates better than a status word
- Cancel/manage must be findable — hiding it violates store policy and breeds chargebacks
- Reorder is the highest-value button on this screen for repeat-purchase businesses

## Technical Considerations
- Paginated orders API with server-computed status; statuses change asynchronously (webhooks from fulfillment/payments)
- Invoice PDFs generated server-side, delivered via short-lived signed URLs
- IAP subscriptions cannot be cancelled in-app — deep-link to the platform's subscription management (App Store/Play) for those; direct billing can cancel in-app
- Dunning states driven by payment-provider webhooks; show grace periods accurately
- Refunds and returns are async — model pending states, don't fake instant results

## References
- Amazon orders, App Store subscription management patterns
