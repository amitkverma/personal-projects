# Confirmation Dialog

> Category: System & Feedback States

## Purpose
Alert requiring explicit consent for risky or destructive actions.

## Key Elements
- Title stating the action as a question ("Delete 3 entries?")
- Body stating consequence and reversibility
- Action button labeled with the verb ("Delete"), destructive-styled
- Cancel as the safe, default-focused option

## States & Variations
- Standard confirm; destructive confirm (red action)
- Typed confirmation ("type DELETE") for catastrophic scope
- "Don't ask again" checkbox for low-stakes repeats

## Design Notes
- Buttons say verbs, never Yes/No — "Cancel / Delete" survives skim-reading
- Follow platform button-position conventions rather than inventing your own
- If an action is easily undoable, prefer act-then-undo (toast) over confirm-then-act — fewer interruptions, same safety

## Technical Considerations
- Use native alert APIs (UIAlertController / MaterialAlertDialog) — focus trapping, a11y, and dismissal behavior come free
- Prefer soft-delete + undo window server-side where possible; it converts confirmations into recoverable actions
- Debounce triggers so double-taps can't stack dialogs
- Persist "don't ask again" per action type, and provide a settings reset
- The confirm action must be idempotent — users double-tap destructive buttons under stress

## References
- Apple HIG Alerts; Material dialogs guidance
