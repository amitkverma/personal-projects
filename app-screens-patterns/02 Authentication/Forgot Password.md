# Forgot Password

> Category: Authentication

## Purpose
Request-and-reset flow for recovering account access.

## Key Elements
- Email/phone entry with a single CTA
- Neutral confirmation screen ("If an account exists, we've sent a link")
- Reset form: new password + confirmation with live rule checking
- Success state routing back to login (or auto-login)

## States & Variations
- Request sent / link opened in-app via deep link / link expired or already used
- Weak-password rejection on the reset form
- Throttled after repeated requests

## Design Notes
- Show the same confirmation whether or not the account exists (anti-enumeration)
- Tell users to check spam; include the "resend" path on the confirmation screen
- Auto-logging the user in after a successful reset removes a frustrating extra login

## Technical Considerations
- Reset tokens: cryptographically random, single-use, short-lived (≤1 hour), stored hashed
- Invalidate all other outstanding reset tokens and (on success) all active sessions
- Email link should be a universal link / app link that opens the in-app reset screen, with a web fallback page for users without the app
- Throttle requests per account and per IP
- Notify the account's email when a reset completes — it's a compromise signal

## References
- OWASP Forgot Password Cheat Sheet
