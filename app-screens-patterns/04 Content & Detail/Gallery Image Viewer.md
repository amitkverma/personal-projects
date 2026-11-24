# Gallery Image Viewer

> Category: Content & Detail

## Purpose
Swipeable full-screen media browsing with zoom.

## Key Elements
- Full-bleed image on a black background
- Horizontal swipe between items with index indicator (3/12)
- Pinch-to-zoom and double-tap zoom
- Share/save actions; swipe-down or × to dismiss

## States & Variations
- Progressive load: cached thumbnail → full resolution
- Zoomed (paging disabled until zoomed out)
- Mixed media (video items with inline playback)
- Load failure per item with retry

## Design Notes
- Interactive dismiss (drag-down with the image following the finger) is expected on iOS
- Chrome (actions, index) auto-hides on tap for uninterrupted viewing
- Preserve the aspect ratio; never crop in the viewer

## Technical Considerations
- Memory is the main risk: downsample images to the display size, never decode full-resolution originals into memory for a phone screen
- Preload only adjacent items (n−1, n+1); evict aggressively as the user swipes
- Reuse the thumbnail already in cache as the instant placeholder, then swap the hi-res
- Save-to-photos needs the add-only photo permission (iOS) / scoped storage handling (Android)
- Gesture arbitration between pinch, pan, page-swipe, and dismiss is fiddly — use a proven library or budget real time

## References
- Photos apps, Instagram media viewer (Mobbin UI patterns)
