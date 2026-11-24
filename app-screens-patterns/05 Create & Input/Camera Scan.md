# Camera Scan

> Category: Create & Input

## Purpose
Capture surface for photos, documents, barcodes, or QR codes.

## Key Elements
- Full-screen viewfinder with mask/guides for the target shape
- Capture button, or auto-detect with visual lock-on
- Torch toggle; gallery-import alternative
- Preview → retake/confirm step

## States & Variations
- Permission primer / denied (manual-entry fallback)
- Scanning / detected (highlight + haptic) / processing (OCR, upload)
- Low-light warning; multi-page document capture
- Barcode vs QR vs document vs photo modes

## Design Notes
- Instant detection feedback (frame highlight + haptic tick) is what makes scanning feel good
- Always offer manual entry — cameras fail on glare, damage, and edge cases
- Keep the guide mask honest about what will actually be captured

## Technical Considerations
- AVFoundation/VisionKit (iOS) or CameraX/ML Kit (Android); on-device barcode/text recognition avoids latency and privacy issues
- Process frames on a background queue and throttle analysis (~10fps is plenty) to avoid thermal throttling and battery drain
- Document capture needs edge detection + perspective correction; VisionKit's document scanner is free on iOS
- Compress and resize before upload; strip EXIF GPS unless location is genuinely needed
- Camera pipelines are a top crash/ANR source — test low-end Android devices and interruption cases (call arrives mid-scan)
- Handle rotation and tap-to-focus; users expect both

## References
- Banking check deposit, WhatsApp QR, Notes document scan patterns
