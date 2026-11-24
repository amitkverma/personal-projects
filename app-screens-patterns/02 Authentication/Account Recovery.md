# Account Recovery

> Category: Authentication

## Purpose
Fallback flow for locked accounts or lost 2FA devices.

## Key Elements
- Recovery-method chooser: backup email/phone, recovery codes, support escalation
- Step indicator for multi-stage identity verification
- Case-submitted confirmation with expected response time
- Forced credential reset on successful recovery

## States & Variations
- Automated recovery available vs manual review required
- Recovery denied (verification failed)
- Success → forced password change + re-issued 2FA

## Design Notes
- Users arrive here stressed — calm, specific copy and honest wait-time estimates matter more than visual polish
- Explain what each verification step proves and why it's needed
- Offer recovery codes at 2FA setup and remind users to store them; this screen is where that pays off

## Technical Considerations
- Recovery codes: generated at 2FA enrollment, one-time use, stored hashed
- Rate-limit aggressively and add friction deliberately — recovery is the classic account-takeover path
- On successful recovery: revoke all sessions and tokens, force credential reset, notify every contact channel on file (fraud tripwire)
- Manual-review cases need a support queue with full audit logging of what evidence was checked
- Keep an immutable audit trail of recovery attempts per account

## References
- NIST 800-63B account recovery guidance
