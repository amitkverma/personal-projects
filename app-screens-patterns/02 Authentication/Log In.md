# Log In

> Category: Authentication

## Purpose
Returning-user entry with credentials, SSO, and a path to password recovery.

## Key Elements
- Identifier (email/phone) + password with show/hide toggle
- SSO buttons mirroring the signup options
- "Forgot password?" link near the password field
- Link to sign up for new users

## States & Variations
- Idle / submitting / invalid credentials
- Account locked or throttled after repeated failures
- Second factor challenge step (OTP/TOTP) after primary success
- Biometric fast-path once previously logged in
- Offline: explain, don't just fail

## Design Notes
- Remember and pre-fill the last identifier
- Use one generic error for bad credentials ("email or password is incorrect") — don't reveal which was wrong
- Surface the biometric option immediately after the first successful manual login

## Technical Considerations
- OAuth2/OIDC-style short-lived access token + refresh token; refresh silently on 401 with single-flight locking so parallel requests don't stampede the refresh endpoint
- Server-side lockout/backoff on failures; client mirrors with disabled CTA and countdown
- Invalidate all sessions server-side on password change; handle the resulting 401s gracefully on other devices
- If a deep link triggered the login, return the user to the original destination afterwards
- Log failed attempts with device/IP metadata for anomaly detection
- Test password-manager autofill on both platforms — broken autofill quietly kills conversion

## References
- OWASP Session Management Cheat Sheet
- Headspace login (Mobbin)
