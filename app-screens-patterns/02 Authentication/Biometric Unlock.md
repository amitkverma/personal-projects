# Biometric Unlock

> Category: Authentication

## Purpose
Face ID / fingerprint gate for quick, secure re-entry.

## Key Elements
- Biometric glyph and short prompt
- Retry button after a failed attempt
- Fallback link: device passcode or account password
- Opt-in toggle surfaced after first manual login

## States & Variations
- Prompt → success (instant continue)
- Failed attempt(s) → OS-level retry/lockout
- Biometrics changed or unenrolled → keys invalidated, password re-auth required
- Hardware unavailable → feature hidden entirely

## Design Notes
- Offer as an opt-in convenience after the first successful login, not as a demand
- Never make biometrics the only path in — fallback must always exist
- Show the app's own lock screen instantly on foreground so content never flashes before the check

## Technical Considerations
- iOS LocalAuthentication / Android BiometricPrompt (use the androidx wrapper for device coverage)
- Protect actual secrets, not just UI: store the refresh token in Keychain with access control (.biometryCurrentSet) or Android Keystore keys with setUserAuthenticationRequired — a lock screen over readable storage is theater
- .biometryCurrentSet / invalidatedByBiometricEnrollment means enrolling a new fingerprint invalidates keys — catch this and fall back to password re-auth with a clear message
- Respect OS lockout states (too many failures → device credential)
- Blur or hide app content in the task switcher when the app is locked

## References
- Apple LocalAuthentication docs; Android BiometricPrompt guide
