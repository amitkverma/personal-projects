# Edit Form

> Category: Create & Input

## Purpose
Pre-filled form for updating an existing record.

## Key Elements
- All fields pre-populated with current values
- Save CTA disabled until something changes (dirty tracking)
- Delete action — visually separated, destructive styling
- Last-updated metadata line

## States & Variations
- Pristine / dirty / saving
- Conflict: the record changed on another device while editing
- Record deleted underneath the editor
- Partial save failure with per-field errors

## Design Notes
- The disabled-until-dirty save button tells users "nothing to save yet" better than words
- Back navigation with unsaved changes must confirm discard
- Keep Delete away from Save; bottom-of-screen, red, with confirmation

## Technical Considerations
- Decide PATCH-diff vs full PUT deliberately and document the semantics — partial-update behavior around omitted fields is a classic source of data-loss bugs (some EHR-style APIs silently null omitted fields)
- Optimistic concurrency: send updatedAt/ETag with If-Match; on 409/412, show a conflict resolution path instead of silently overwriting
- Deep-copy the initial state for dirty comparison; don't mutate the original
- Handle 404 on save (deleted elsewhere) with a clear exit, not a stuck spinner
- Auto-save vs explicit-save is a product decision — mixing both confuses users

## References
- Eight Sleep edit-sleep-session (Mobbin) — clean timestamp editing
