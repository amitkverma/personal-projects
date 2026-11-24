# Create New

> Category: Create & Input

## Purpose
Form or composer for adding a post, entry, log, or task.

## Key Elements
- Fields appropriate to the entity, most-important first
- Smart defaults (timestamp = now, last-used values)
- Media attach (photo/file) where relevant
- Save/submit CTA; cancel with discard confirmation when dirty

## States & Variations
- Empty with defaults / dirty / validating / submitting
- Offline: saved locally, queued for sync
- Success (toast + return, or detail view)
- Failure with inputs fully preserved

## Design Notes
- Default everything defaultable — a baby-feed log should be one tap for the common case, editable for the exceptions
- One screen for ≤5 fields; switch to a wizard beyond that
- Put the keyboard-summoning field first and focus it automatically when the form is the screen's whole purpose

## Technical Considerations
- Autosave drafts locally so process death or an accidental swipe never loses input
- Optimistic insert into the local store, then background sync with retry/backoff — the UI should never wait on the network for a log entry
- Idempotency keys (client-generated UUID per submission) so retries can't create duplicates
- Keep client and server validation rules in parity; surface server rejections field-by-field
- Media: compress client-side before upload; use resumable uploads for large files
- Emit a created event on a local bus/store so lists refresh without a refetch

## References
- timespent add-session, Oura log-a-dose (Mobbin)
