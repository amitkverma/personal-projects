# Multi-step Wizard

> Category: Create & Input

## Purpose
Stepper flow that breaks a long task into sequential screens.

## Key Elements
- Progress indicator: bar, dots, or "Step 2 of 5"
- One decision or topic per screen
- Back navigation that preserves input
- Review/summary step before final submit

## States & Variations
- Linear vs branching (conditional steps based on answers)
- Resumed mid-flow after abandonment
- Per-step validation errors
- Save-and-exit for long flows (KYC, listings)

## Design Notes
- Progress must be honest — a bar that jumps from 80% to "3 more steps" destroys trust
- Group related inputs; five two-field steps beat two five-field steps on mobile
- The review step is where users catch mistakes; make every section editable from there

## Technical Considerations
- Model the flow as an explicit state machine (states, transitions, guards) — branching logic in navigation callbacks becomes unmaintainable fast
- Persist wizard state locally keyed by a draft ID; offer resume on return
- Validate per step at the boundary, but re-validate everything server-side at submit
- Submit once at the end; for very long flows, checkpoint to the server per section
- System back button/gesture must behave identically to the on-screen back
- Funnel analytics per step; drop-off location is the single most actionable metric here

## References
- Headspace onboarding quiz flow, Apple Health add-pregnancy flow (Mobbin)
