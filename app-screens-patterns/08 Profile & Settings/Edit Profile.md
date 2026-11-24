# Edit Profile

> Category: Profile & Settings

## Purpose
Form for changing avatar, name, and profile fields.

## Key Elements
- Avatar changer: camera / gallery / remove, with crop
- Fields: display name, handle, bio (with character counter), links
- Handle availability indicator
- Save (disabled until dirty)

## States & Variations
- Pristine / dirty / saving / saved
- Handle taken / invalid characters
- Avatar uploading with progress; upload failed with retry

## Design Notes
- Preview changes live (the header updates as you type)
- Show character counters only near the limit
- Handle-change consequences (old links break?) deserve a confirmation line

## Technical Considerations
- Avatar: crop square client-side, resize (~512px), compress, background-upload with optimistic display; keep the old image until the new one is confirmed on CDN
- Handle availability: debounced server check; final uniqueness enforced at save (race-safe unique constraint), with a clear conflict error
- Server-side validation for bio/links (profanity, URL schemes, length in bytes vs characters — emoji count differently)
- PATCH only changed fields; return the canonical record and update local cache from it

## References
- Standard social edit-profile patterns (Mobbin)
