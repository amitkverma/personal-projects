# Paywall Plan Selection

> Category: Commerce & Payments

## Purpose
Subscription tiers, trial explainer, and purchase CTA.

## Key Elements
- Plan cards: annual (highlighted, savings badge) vs monthly
- Benefit list or feature-comparison table
- Trial timeline explainer (today → reminder day → charge day)
- Price with clear billing terms; single purchase CTA
- Restore Purchases link; Terms/Privacy links

## States & Variations
- Trial-eligible vs returning (no trial) pricing
- Intro/promotional offer variant
- Purchasing / success / user-cancelled
- Regional pricing and currency
- Hard paywall vs dismissible

## Design Notes
- Anchor with the annual plan's savings; preselect it
- The "how your trial works" timeline (Headspace/Blinkist pattern) measurably reduces trial anxiety — show exactly when charging happens and how to cancel
- Transparent renewal terms aren't just ethics; app review requires them

## Technical Considerations
- StoreKit 2 (iOS) / Play Billing (Android); digital content **must** use in-app purchase per store rules — external payment links get apps rejected
- Server-side receipt/purchase-token validation is the source of truth for entitlements; the client only caches it
- Handle the ugly paths: pending transactions, interrupted purchases, restore, family sharing, refunds revoking access
- Pull localized prices from the store APIs — never hardcode or convert currencies yourself
- Process store webhooks/server notifications for renewals, cancellations, grace periods, and billing retries; entitlement state is an event stream, not a boolean
- Make paywall layout/copy remotely configurable — it will be your most A/B-tested screen
- Test the full matrix in sandbox: new, renew, cancel, refund, restore, upgrade/downgrade proration

## References
- Headspace trial paywall with timeline (Mobbin)
- RevenueCat docs (good ecosystem overview even if not using it)
