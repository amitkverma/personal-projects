# OTP Verification

> Category: Authentication

## Purpose
One-time code entry to verify email or phone ownership.

## Key Elements
- 4–6 digit code entry rendered as separate boxes
- Masked destination ("code sent to a•••@example.com")
- Resend button with cooldown countdown
- "Change email/number" escape hatch
- Auto-submit when the last digit is entered

## States & Variations
- Waiting for input / auto-filled from SMS or mail
- Wrong code (shake + clear), expired code, too many attempts
- Resend cooldown active
- Voice-call fallback for SMS delivery failures

## Design Notes
- One invisible input styled as boxes beats six real inputs (paste, backspace, and a11y all work better)
- Show the destination so users know which inbox to check
- Auto-advance and auto-submit remove two taps from every verification

## Technical Considerations
- iOS: set textContentType = .oneTimeCode for SMS autofill; Android: SMS Retriever / User Consent API (no SMS-read permission needed)
- Codes: ≥6 digits, single-use, short expiry (5–10 min), stored hashed, max ~5 attempts then invalidate
- Rate-limit resends server-side; the client countdown must be computed from a timestamp so backgrounding doesn't reset it
- Support paste of the full code
- Deliverability: SMS/email delivery fails often — log delivery provider callbacks and expose the resend + change-destination paths prominently

## References
- Standard OTP pattern; Twilio/Firebase Auth verification docs
