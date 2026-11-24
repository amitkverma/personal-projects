# Contacts Invite Referral

> Category: Communication & Social

## Purpose
Friend list, invite mechanics, and referral rewards.

## Key Elements
- Referral code/link with one-tap copy
- Share CTA opening the system share sheet
- Two-sided incentive explainer ("You get X, they get Y")
- Invite-status list (sent, joined, reward earned)
- Optional contact picker

## States & Variations
- No invites yet / pending / converted with rewards
- Reward redemption flow; referral cap reached
- Campaign variants (seasonal boosts)

## Design Notes
- State both sides' rewards explicitly — one-sided offers convert poorly
- Show progress toward the next reward (goal gradient)
- Never require contact-book access; a shareable link is the baseline path

## Technical Considerations
- Attribution needs deferred deep linking (link → store → install → open) via Branch/AppsFlyer or your own referral-code entry fallback at signup
- Anti-fraud from day one: self-referral detection (device fingerprint, payment identity), velocity caps, reward clawback capability
- Reward issuance is a server-side, idempotent operation with an auditable ledger
- Contact upload (if offered) requires permission plus a real privacy story — hash identifiers, delete after matching
- Referral state machine: invited → installed → activated → rewarded; define "activated" precisely (signup? first purchase?)

## References
- Dropbox referrals (the classic), Revolut invites (Mobbin)
