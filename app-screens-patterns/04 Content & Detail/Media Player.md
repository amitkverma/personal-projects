# Media Player

> Category: Content & Detail

## Purpose
Full-screen audio/video playback with scrubber and transport controls.

## Key Elements
- Artwork or video surface; ambient background for audio (Headspace's layered gradients)
- Big play/pause; skip ±15s; scrubber with elapsed/remaining
- Speed control, captions toggle, AirPlay/Cast, share
- Close/minimize into a mini-player

## States & Variations
- Loading/buffering, playing, paused, seeking
- Completed → summary/next-item screen (retention lever)
- Background/lock-screen playback with system controls
- Mini-player docked above the tab bar
- Error (stream failed) with retry and offline hint

## Design Notes
- One giant primary control; auto-hide chrome for video after ~3s
- The completion screen is prime real estate: stats, streak, next session (see Headspace "Minutes Meditated")
- Sleep timers and captions matter enormously in wellness/audio apps

## Technical Considerations
- AVPlayer (iOS) / Media3 ExoPlayer (Android); enable background-audio entitlement and audio session category correctly
- MediaSession + Now Playing info for lock-screen/notification/headphone/watch controls — table stakes
- Handle interruptions (calls, Siri, other apps) and audio-focus changes: pause and resume correctly
- Persist playback position every few seconds for resume; report progress to the server for cross-device continuity
- Streaming: HLS/DASH with adaptive bitrate; downloads need DRM decisions if content is paid
- Analytics: play start, completion, drop-off position — the drop-off curve is the content team's main tool

## References
- Headspace player: length picker, captions, haptic assistance (Mobbin)
