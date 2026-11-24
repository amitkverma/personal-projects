# Privacy & Data

> Category: Profile & Settings

## Purpose
Data sharing controls, permissions review, and export/delete requests.

## Key Elements
- Toggles: analytics, personalization, ad tracking — each with plain-language effect descriptions
- Connected third parties list with disconnect
- Download-my-data request; delete-account entry point
- Policy links; consent history

## States & Variations
- Export requested (pending, may take days) → ready with download link
- Toggles saving/synced
- Region-specific rows (CCPA "do not sell", GDPR rights)

## Design Notes
- Describe what each toggle actually changes for the user, not legal categories
- Export and delete must be genuinely findable — burying them violates GDPR/CCPA expectations
- Consent changes should confirm what just happened

## Technical Considerations
- Consent flags must actually propagate at runtime: analytics opt-out disables SDK collection (not just a server flag), ATT status gates IDFA on iOS, consent mode configured in analytics/ads tools
- Data export as an async server job: compile → notify → expiring signed URL; authenticate the download
- Deletion: grace period, then a real cascade across services, backups policy documented; issue deletion to third-party processors too
- Regional logic server-driven (which rights UI to show per jurisdiction)
- Log consent state transitions immutably — they are legal records

## References
- GDPR Art. 15–17 (access, erasure); Apple ATT documentation
