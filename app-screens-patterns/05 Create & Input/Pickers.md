# Pickers

> Category: Create & Input

## Purpose
Date, time, duration, or amount selectors, usually presented as bottom sheets.

## Key Elements
- Bottom-sheet presentation with grabber and Confirm/Cancel
- Control matched to the type: calendar (dates), wheel (time/duration), stepper or slider (amounts)
- Quick presets for the common case (Today, Now, +15 min, last-used amount)
- Live display of the currently selected value

## States & Variations
- Default value pre-selected; min/max bounds enforced
- Disabled options (past dates, unavailable slots)
- Keyboard-entry alternative for power users
- Unit-switchable amounts (ml/oz, kg/lb)

## Design Notes
- Native controls beat custom ones: users already know them and accessibility is free
- Presets should cover the 80% case in one tap
- Show the consequence of the selection where relevant ("ends at 3:45 PM")

## Technical Considerations
- Prefer platform pickers (UIDatePicker, MaterialDatePicker, Compose/SwiftUI equivalents) for locale, a11y, and maintenance
- Store timestamps as UTC + capture the timezone; display in local time — and respect the locale's 12/24h clock and first day of week
- Amounts: store one canonical unit, convert only at display; never store "7" without knowing if it was ml or oz
- Bottom sheet + keyboard together cause layout jumps — test the keyboard-entry path explicitly
- Clamp and validate bounds in the picker itself; don't let invalid values reach the form

## References
- Headspace session-length sheet (3/5/10 min presets) (Mobbin)
