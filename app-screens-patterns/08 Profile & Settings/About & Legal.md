# About & Legal

> Category: Profile & Settings

## Purpose
Version info, terms of service, privacy policy, and licenses.

## Key Elements
- App version + build number (tap to copy)
- Terms of Service, Privacy Policy rows
- Open-source licenses list
- Company info, website, social links

## States & Variations
- Mostly static; license list length varies
- Regional legal documents where required

## Design Notes
- Pure utility list — no marketing needed here
- Nobody reads licenses, but the row is legally required by many OSS licenses
- Tap-to-copy version is a small support superpower

## Technical Considerations
- Serve legal docs as web views pointing at canonical URLs so updates don't need releases; cache a fallback for offline
- Auto-generate the OSS license list from the dependency graph at build time (SPM/Gradle license plugins) — hand-maintained lists drift instantly
- Expose version, build, and commit hash programmatically (also to the support pre-fill)
- The classic hidden dev menu (7 taps on version) must be excluded or auth-gated in production builds

## References
- Android/iOS license-plugin docs
