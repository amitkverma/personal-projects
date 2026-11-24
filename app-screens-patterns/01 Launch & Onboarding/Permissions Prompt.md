# Permissions Prompt

> Category: Launch & Onboarding

## Purpose
Contextual primer plus system dialog requesting notifications, location, camera, or health access.

## Key Elements
- Custom primer screen: illustration, concrete benefit copy, Allow CTA, "Not now"
- The OS permission dialog itself (system-controlled)
- Settings deep-link fallback when previously denied
- Example of what the permission enables (e.g. a sample notification)

## States & Variations
- Never asked / primer shown / granted / denied
- Permanently denied → requires Settings app round-trip
- iOS provisional (quiet) notification authorization as a middle path
- Per-permission variants: notifications, location (while-in-use vs always), camera, photos, health

## Design Notes
- Ask in context: notifications after the first successful session, camera when the user taps scan — never stack prompts at launch
- A good primer measurably raises grant rates; "Not now" must be a real option
- Never punish denial; keep the feature reachable with manual alternatives

## Technical Considerations
- Always check current authorization status before prompting; branch UI accordingly
- iOS: you get exactly one real OS prompt per permission — gate it behind primer acceptance; afterwards only the Settings deep link (UIApplication.openSettingsURLString) works
- Android 13+: POST_NOTIFICATIONS is a runtime permission; use shouldShowRequestPermissionRationale to detect "denied forever"
- Re-check status on every app foreground — users change settings outside the app
- Track primer-shown → OS-prompt → granted conversion as a funnel
- Keep a per-permission "last asked" timestamp to cap re-prompting frequency

## References
- Headspace notification primer with example toggles (Mobbin)
- Apple HIG — Requesting permission; Android permission UX guidelines
