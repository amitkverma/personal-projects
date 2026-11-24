# Rewards & Coupons

> Category: Engagement & Growth

## Purpose
Points balance, redeemable perks, and offers.

## Key Elements
- Points/credit balance header with earn-history link
- "Ways to earn" action list
- Redemption catalog with point costs and value equivalents
- Coupon cards: code, discount, expiry, terms
- Redemption history

## States & Variations
- Zero balance (emphasize earning paths)
- Sufficient vs insufficient points per catalog item
- Coupon active / applied / used / expired
- Redemption processing / failed / reversed

## Design Notes
- Make the earn loop obvious; a rewards tab users don't understand is dead weight
- Expiring-soon coupons deserve a badge and a nudge
- Show real-money equivalents where possible ("500 pts ≈ $5")

## Technical Considerations
- Points as an append-only transaction ledger (earn/redeem/expire entries), never a mutable balance column — this gives auditability, race safety, and dispute resolution
- Redemption is an atomic, idempotent server transaction: check balance → debit → issue reward, with rollback on issue failure
- Coupon enforcement server-side: single-use locks, expiry evaluated in a defined timezone, stacking rules explicit
- Fraud controls: earn-velocity caps, device/account linkage checks, clawback capability
- Finance visibility: outstanding points are a liability — build the reporting query before accounting asks
- Expiry jobs need advance-warning notifications, not silent removal

## References
- Starbucks Rewards as the reference loyalty UX
