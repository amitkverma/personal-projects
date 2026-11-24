# Account & Security

> Category: Profile & Settings

## Purpose
Password, 2FA, active sessions, and connected accounts.

## Key Elements
- Email/phone rows with verified badges and change flows
- Change password
- Two-factor authentication setup (authenticator app, SMS) + recovery codes
- Active sessions/devices list with revoke
- Connected accounts (Google/Apple) link/unlink

## States & Variations
- 2FA off / enrolling (QR + confirm code) / on
- Session list with current-device marker; revoked session
- Unlink blocked because it's the last sign-in method

## Design Notes
- Verified vs unverified must be visually obvious with a one-tap fix
- Explain consequences before changes ("this signs out all devices")
- Recovery codes: force an acknowledgment that they're saved

## Technical Considerations
- Require recent re-authentication (password or biometric) before any change on this screen
- TOTP enrollment: standard otpauth:// URI in a QR + manual key fallback; verify one code before enabling; generate hashed one-time recovery codes
- Sessions require server-side token registry; revoke = immediate token invalidation, not just list removal
- Guard the invariant "at least one working sign-in method" server-side
- Email every security change to the account (password changed, new device) — compromise tripwire
- Audit-log all actions on this screen

## References
- Google Account security page as the reference implementation
