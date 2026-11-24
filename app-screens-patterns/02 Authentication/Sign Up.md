# Sign Up

> Category: Authentication

## Purpose
Account creation via email/phone form with SSO options and legal consent.

## Key Elements
- Minimal field set: email (or phone) + password; name optional or deferred
- SSO buttons: Apple, Google, and others relevant to the audience
- Terms of Service / Privacy Policy consent line
- Inline validation with password rules shown upfront
- "Already have an account? Log in" link

## States & Variations
- Empty / typing with live validation / field-level errors
- Submitting (disabled CTA + spinner)
- Duplicate account error with a pivot to login
- Success → email/OTP verification step
- SSO-first variant where the email form is secondary

## Design Notes
- Every extra field costs conversion; collect profile data later (progressive profiling)
- Show password requirements before the first failure, not after
- iOS rule of thumb: offering any third-party social login requires offering Sign in with Apple
- Keep the legal consent visible but compact; pre-checked boxes are illegal in some regions

## Technical Considerations
- Validate client-side for UX, but enforce everything server-side; never trust the client
- Passwords hashed with bcrypt/argon2 server-side; never logged, never stored recoverable
- Return generic errors publicly but handle duplicate-email safely to avoid account enumeration (e.g. "check your email" flows)
- Rate-limit signups per IP/device; add bot protection (captcha) after suspicious volume
- Plan SSO account-linking from day one: the same email arriving via Google and via password must converge on one account
- Store issued tokens in Keychain (iOS) / EncryptedSharedPreferences or Keystore-backed storage (Android)
- Set textContentType/autofill hints so password managers can generate and save credentials

## References
- Headspace sign-up with SSO + inline validation (Mobbin)
- OWASP Authentication Cheat Sheet
