# Splash Screen

> Category: Launch & Onboarding

## Purpose
Branded launch frame shown while the app initializes; sets tone and masks load time.

## Key Elements
- App logo or wordmark, centered on a brand-color background
- Optional tagline or mascot animation
- Loading indicator — only if the wait exceeds ~2 seconds
- Subtle version number (optional, helps support)

## States & Variations
- Warm start: dismisses almost instantly, no spinner
- Cold start with data sync: extended state with progress indication
- First run: may hand off to onboarding instead of home
- Blocked: hands off to Force Update or maintenance screen

## Design Notes
- Match the static system launch screen exactly so there is no visual "jump"
- Keep it under ~2s perceived time; users blame the app, not the network
- No ads, no marketing copy — this is a utility moment
- Provide light/dark variants that follow the system theme

## Technical Considerations
- iOS: the launch screen is a static storyboard (no code runs); any animated splash is a separate first view controller shown after launch
- Android 12+: use the SplashScreen API rather than a custom Activity
- Do token refresh, remote config, and feature-flag fetches behind the splash **with a timeout** — never block indefinitely on network; fall back to cached values
- Centralize routing decisions (onboarding vs login vs home vs force-update) in a single launch coordinator so the logic lives in one place
- Measure cold-start time-to-interactive as a tracked performance metric
- Defer all non-critical SDK initialization until after first frame

## References
- Apple HIG — Launching; Android SplashScreen API docs
- Headspace splash (Mobbin): simple logo-on-white
