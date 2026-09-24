# Backlog: Dupe Twin MVP

**Format:** User stories · **Source:** `docs/05-prd-dupe-twin-mvp.md` (v2) + pre-mortem mitigations from `docs/06`
**Total stories:** 24 (across 7 epics + 2 spikes) · **Sequenced for:** solo founder, ~10 weeks
**Effort scale:** S ≤ 1 day · M = 2–3 days · L = 4–5 days
**🪜 = on the descope ladder** (cut order per `docs/06` T3: 🪜4 first, 🪜1 last-resort never)

---

## Spikes (week 1 — before contracts or code)

#### SPIKE-1: Scan vendor webview + pricing validation
Test Haut.AI and Perfect Corp browser SDKs inside Instagram/YouTube in-app webviews (Android + iOS); obtain real per-scan pricing; audit accuracy on Indian skin tones.
- [ ] Camera capture attempted in Instagram + YouTube webviews on Android Chrome-webview (primary — India is ~95% Android) and iOS Safari-webview; results documented per vendor
- [ ] "Open in browser" hand-off flow prototyped and timed if webview capture fails
- [ ] Per-scan blended cost modeled at 1k/10k/100k scans; pass = <₹5/scan (~$0.06)
- [ ] Vendor accuracy spot-checked on Indian skin tones (Fitzpatrick IV–VI) — mis-scoring pigmentation/acne is disqualifying
- [ ] Go/no-go recommendation per vendor + fallback vendor named

Priority: P0 | Effort: M | Dependencies: none | *Pre-mortem T2, T4*

#### SPIKE-2: Data sourcing legal + ground-truth set
- [ ] Legal read documented on scraping/attributing INCI lists + Indian retailer prices (Nykaa, Amazon.in, Flipkart, Purplle) (F3)
- [ ] 50 community-consensus dupe pairs collected with sources (r/IndianSkincareAddicts threads, Skinskool/SkinSort agreement, Indian dupe creators) — India-relevant pairs (Indian D2C twins of prestige/K-beauty) prioritized — as the engine eval set
- [ ] DPDP legal review kicked off (counsel engaged; consent flow, 18+ gate, vendor DPA, cross-border processing questions submitted)

Priority: P0 | Effort: M | Dependencies: none | *Pre-mortem T1; PRD open questions*

---

## Epic 1 — Fit+Price Engine (weeks 1–2) · **HARD GATE: no UI work until E1-3 passes**

#### E1-1: Ingredient similarity scorer
As the founder, I want a deterministic ingredient-similarity score between any two products, so that dupe ranking has an explainable core.
- [ ] Parses INCI lists; normalizes synonyms (e.g., "aqua"/"water") via a maintained alias table
- [ ] Weights actives above excipients; respects INCI ordering as a concentration proxy
- [ ] Outputs 0–100 match score + the shared/missing key actives that produced it (explainability payload)
- [ ] Pure function with unit tests; no network calls

Priority: P0 | Effort: L | Dependencies: SPIKE-2 (alias/actives references)

#### E1-2: Profile fit filter + price ranking
As Maya, I want dupes filtered by my sensitivities and ranked by fit×price, so results are personal, not generic.
- [ ] Hard-excludes products containing user's flagged allergens/sensitivities (fragrance, essential oils, etc.)
- [ ] Ranking = match score × price-per-use (price ÷ size); ties broken by price
- [ ] Personal-fit flags computed per result ("fragrance-free ✓ — matches your profile")
- [ ] Budget ceiling from profile caps results

Priority: P0 | Effort: M | Dependencies: E1-1

#### E1-3: Ground-truth eval harness 🚦
As the founder, I want automated scoring of the engine against 50 known dupe pairs, so I know it's credible before building UI.
- [ ] Harness runs engine over eval set; reports top-1 and top-3 agreement with community consensus
- [ ] **Gate: ≥80% agreement or all downstream UI epics pause** (fix engine first)
- [ ] Failure analysis output: which pairs missed and why (drives weight tuning)
- [ ] Re-runnable in <5 min for iteration

Priority: P0 | Effort: M | Dependencies: E1-1, E1-2, SPIKE-2

---

## Epic 2 — Product Database & Ops (weeks 2–4)

#### E2-1: Product data model + seed pipeline
As the founder, I want ~500 India-relevant products with INCI lists and ₹ prices from 3 retailers loaded, so launch-cohort searches mostly succeed.
- [ ] Schema: product, brand, INCI list (ordered), sizes, MRP + per-retailer selling price + URL + fetched-at timestamp (MRP vs. discounted price tracked separately — Indian sale cycles swing them apart)
- [ ] Seed list driven by concierge demand data + Reels-viral SKUs + Nykaa bestsellers (not editorial guess — pre-mortem T5); mix covers Indian D2C (Minimalist, The Derma Co, Dot & Key…), K-beauty-in-India, and Nykaa-available prestige
- [ ] 500 products loaded with ≥95% having complete INCI + ≥2 retailer prices
- [ ] Import is idempotent and re-runnable

Priority: P0 | Effort: L | Dependencies: SPIKE-2 (legal read)

#### E2-2: Hot-add admin path
As the founder, I want to index a new trending product in <15 minutes, so same-day viral products are searchable.
- [ ] Admin-only form: paste INCI + prices → product live immediately
- [ ] Validation catches malformed INCI; preview of computed matches before publish
- [ ] Audit log of additions

Priority: P0 | Effort: M | Dependencies: E2-1

#### E2-3: Price refresh job 🪜(P1)
As Maya, I want prices to be current, so the savings numbers are real.
- [ ] Scheduled refresh per retailer (Nykaa, Amazon.in, Flipkart, Purplle); staleness timestamp stored and shown in UI
- [ ] Alert when >10% of catalog exceeds 7-day staleness (pre-mortem T11 trigger); expect spikes around sale events (Pink Friday, Big Billion Days)
- [ ] Graceful per-retailer failure (one broken scraper doesn't blank all prices)

Priority: P1 | Effort: L | Dependencies: E2-1

---

## Epic 3 — Auth, Profile & Onboarding (weeks 2–4)

#### E3-1: Magic-link auth + waitlist import
As Maya, I want to sign in with just my email, so there's zero password friction.
- [ ] Email magic link: request → click → session; links expire in 15 min, single-use
- [ ] Waitlist emails importable as pre-authorized invites; non-invited emails see waitlist page
- [ ] Session persists across visits on same device

Priority: P0 | Effort: M | Dependencies: none

#### E3-2: Skin-profile quiz
As Maya, I want a ≤60-second quiz capturing what a scan can't see, so my results reflect my sensitivities and budget.
- [ ] ≤6 questions: skin type, top-2 concerns, sensitivities/allergens, budget ceiling
- [ ] Median completion ≤60s (measured); progress indicator; editable later from settings
- [ ] Profile persisted and versioned (changes don't corrupt past journal correlations)

Priority: P0 | Effort: M | Dependencies: E3-1

#### E3-3: Face scan capture behind feature flag
As Maya, I want to scan my face in the browser and get my skin analysis, so onboarding feels magical.
- [ ] **Feature-flagged: app fully functional quiz-only when flag is off** (pre-mortem insurance policy)
- [ ] Consent screen before camera access (counsel-approved, DPDP-compliant language); 18+ age gate (DPDP treats under-18s as children requiring parental consent — we exclude them); flag stays off until DPDP counsel review clears
- [ ] Lighting/framing guidance; retake loop; results <30s
- [ ] Raw image deleted post-processing — only derived metrics stored; deletion logged
- [ ] Webview detection → designed "open in browser" hand-off (per SPIKE-1 findings) with its own funnel event

Priority: P0 | Effort: L | Dependencies: SPIKE-1, E3-2, vendor contract

#### E3-4: Merged skin profile + scan results screen
As Maya, I want one profile combining scan findings and quiz answers, so everything downstream is personalized.
- [ ] Scan metrics + quiz answers merge into a single profile object consumed by engine and routine builder
- [ ] Results language is observational ("what we noticed"), shows confidence levels, never diagnostic (pre-mortem T7)
- [ ] In-product "this looks wrong" flag on scan results; flags human-reviewed in launch cohort

Priority: P0 | Effort: M | Dependencies: E3-2 (E3-3 optional via flag)

---

## Epic 4 — Dupe Lookup & Receipts (weeks 4–6)

#### E4-1: Product search
As Maya, I want to find any popular product as I type, so lookup feels instant.
- [ ] Search-as-you-type over seeded catalog (name, brand, nickname aliases like "TDC" for The Derma Co…); <200ms perceived on mid-range Android over 4G
- [ ] Zero-result path: "not yet indexed — notify me" logs the query + email (feeds E2-2 triage)
- [ ] Lookup-success event instrumented (target ≥85%)

Priority: P0 | Effort: M | Dependencies: E2-1

#### E4-2: Dupe results + explanation card
As Maya, I want the top cheap twins for my skin with a plain-language why, so I can trust the swap.
- [ ] Top 1–3 dupes with ₹ price, price-per-ml, match %, personal-fit flags
- [ ] Explanation card: shared key actives, notable differences, allergen warnings from profile
- [ ] Patch-test prompt + persistent "formulation match ≠ identical results" disclaimer (chemist-advisor-approved copy)
- [ ] "I'd buy this" action + retailer click-out, both instrumented (the core validation metric)

Priority: P0 | Effort: L | Dependencies: E1-3 gate passed, E4-1, E3-4

#### E4-3: Savings receipt generator
As Maya, I want a shareable image of my savings, so I can post my find.
- [ ] Single-swap receipt: original vs. twin, ₹ saved, match % — rendered as downloadable/shareable image
- [ ] Routine receipt: full routine original total vs. optimized total ("₹12,000 → ₹3,500") 🪜(cut #3)
- [ ] One-tap share/download with WhatsApp share intent first-class (India's default forward channel); share events instrumented (target ≥10%)
- [ ] Brand mark present but subtle

Priority: P0 (single-swap) / P1 (routine) | Effort: M | Dependencies: E4-2 (routine variant also needs E5-1)

#### E4-4: Bad-dupe feedback 🪜(P1)
As Maya, I want to flag a dupe that didn't work, so recommendations improve.
- [ ] One-tap "didn't work for me" + reason picker (broke me out, texture, no results…)
- [ ] Feedback joined to profile + swap in the data model (the flywheel seed)

Priority: P1 | Effort: S | Dependencies: E4-2

---

## Epic 5 — Routine Builder (weeks 4–6)

#### E5-1: Routine generation
As Maya, I want an AM/PM routine built for my profile and budget, so I know exactly what to use.
- [ ] Rule-based templates: skin type × concerns × budget → ordered steps (cleanser → treatment → moisturizer → SPF…)
- [ ] Each slot pre-filled by fit+price engine within budget; total routine cost displayed
- [ ] Conflict rules respected (e.g., retinoid + AHA not same slot) — chemist-advisor-reviewed rule table

Priority: P0 | Effort: L | Dependencies: E1-3 gate, E2-1, E3-4

#### E5-2: Routine editing
As Maya, I want to swap/remove/add products in my routine, so it reflects what I actually own.
- [ ] Any slot: accept suggestion, pick alternative from dupe results, mark "already own it," or remove
- [ ] Owned products searchable from catalog; routine cost updates live
- [ ] Edits instrumented (which slots get rejected → engine feedback)

Priority: P0 | Effort: M | Dependencies: E5-1, E4-2

#### E5-3: Daily AM/PM check-off
As Maya, I want to tick off my routine morning and night, so consistency is visible.
- [ ] AM/PM checklists from current routine; one-tap complete-all
- [ ] Streak counter; IST day boundaries (single-timezone market — keep it simple)
- [ ] Check-off events instrumented (habit metric)

Priority: P0 | Effort: M | Dependencies: E5-1

---

## Epic 6 — Journal & Progress (weeks 6–8)

#### E6-1: Daily skin check-in
As Maya, I want a ≤20-second daily journal entry, so tracking never feels like a chore.
- [ ] Skin-feel rating (1–5) + optional tags (breakout, dryness, new product…) + optional note
- [ ] Optional photo 🪜(cut #2): private to user, deletable anytime, stored outside biometric pipeline
- [ ] Completes in ≤20s median (usability-tested per pre-mortem T6); editable same-day

Priority: P0 | Effort: M | Dependencies: E3-1

#### E6-2: Progress timeline + re-scan comparison
As Maya, I want to see my skin's trajectory, so I believe the swaps are working.
- [ ] Timeline of check-ins, routine adherence, and scans
- [ ] Monthly re-scan prompt; side-by-side metric comparison vs. prior scan (flag-dependent)
- [ ] Swap-outcome callout: "redness score improved since switching to [dupe]" — only shown with ≥2 scans + adherence data; observational language

Priority: P0 | Effort: L | Dependencies: E6-1, E5-3 (scan comparison needs E3-3)

#### E6-3: Reminders 🪜(cut #4 → email-only)
As Maya, I want a gentle daily nudge, so the habit sticks without nagging.
- [ ] Channel choice at setup: web push default (Android Chrome majority — reliable in India) with email fallback for iOS Safari users; WhatsApp Business API evaluated post-MVP (per-message cost)
- [ ] AM/PM timing controls; one-tap disable — no guilt copy, no dark patterns
- [ ] Reminder→check-in conversion instrumented

Priority: P0 (email) / P1 (push) | Effort: M | Dependencies: E6-1

#### E6-4: Streaks & milestones 🪜(cut #1)
As Maya, I want streaks and milestones, so consistency feels rewarding.
- [ ] Streak badges; "4 weeks consistent" milestone; shareable progress card
- [ ] Never shames a broken streak (anti-Lóvi tone)

Priority: P1 | Effort: S | Dependencies: E5-3, E6-1

---

## Epic 7 — Launch Readiness (weeks 8–10)

#### E7-1: Per-subsystem funnel analytics
As the founder, I want every subsystem's funnel measurable independently, so a mixed result is diagnosable (pre-mortem E1).
- [ ] Event taxonomy implemented: onboarding (scan/quiz), engine (search→results→accept→click-out), routine (generate→edit→check-off), journal (check-in→streak→re-scan), sharing
- [ ] No PII beyond email; no raw images anywhere in analytics
- [ ] One dashboard: PRD success metrics vs. targets, per cohort week

Priority: P0 | Effort: M | Dependencies: events built incrementally in each epic; this story is the dashboard + taxonomy audit

#### E7-2: Webview & device QA pass
As Maya, I want the app to work where I actually open it, so first sessions don't die.
- [ ] Full-funnel test in Instagram + YouTube webviews and mobile Chrome/Safari (Android-first, then iOS)
- [ ] Scan hand-off flow ≥70% completion in test or scan flag stays off at launch
- [ ] Lighthouse mobile performance ≥80 on core pages, verified on a mid-range Android over 4G (the beachhead's actual device/network)

Priority: P0 | Effort: M | Dependencies: all P0 epics

#### E7-3: Go/no-go checklist + invite rollout
As the founder, I want a gated launch, so no blocker ships to real users.
- [ ] `docs/06` go/no-go checklist executed and evidenced (legal sign-off, vendor cost, scoring gate, concierge baseline, advisor named)
- [ ] Invites in batches (50/50/100) with daily metric review between batches
- [ ] Rollback plan tested: scan flag off, invites pausable

Priority: P0 | Effort: S | Dependencies: everything

---

## Story Map (build order)

```
Wk 1–2   SPIKE-1  SPIKE-2  E1-1 → E1-2 → E1-3 🚦gate
Wk 2–4   E2-1 → E2-2       E3-1 → E3-2 → E3-3(flag) → E3-4
Wk 4–6   E4-1 → E4-2 → E4-3      E5-1 → E5-2 → E5-3
Wk 6–8   E6-1 → E6-2 → E6-3      [P1s if on schedule: E2-3, E4-4, E6-4]
Wk 8–10  E7-1 → E7-2 → E7-3 → launch batches
```
Descope ladder (executed top-down if week 6 slips >5 days): E6-4 → E6-1 photos → E4-3 routine receipt → E6-3 push (email only). Never cut: engine, lookup, basic check-in, analytics.

## Technical Notes

- **Engine is a pure library** with the eval harness as its test suite — keeps the 🚦gate honest and the explainability payload reusable across lookup, routine, and receipts.
- **Scan flag is architectural**, not cosmetic: profile object must be complete from quiz alone; every scan-dependent UI element needs a flag-off state.
- **Analytics events ship inside each story** (acceptance criteria above); E7-1 is the audit + dashboard, not a retrofit.
- **Profile versioning** (E3-2) matters for E6-2 correlations — don't skip it.

## Open Questions (blocking specific stories)

| Question | Blocks | Needed by |
|---|---|---|
| Vendor choice + contract (SPIKE-1 outcome, incl. Indian-skin-tone audit) | E3-3 | Week 2 |
| Counsel-approved DPDP consent copy + compliance ruling | E3-3 launch state | Week 8 |
| Chemist/derm advisor: disclaimer copy + conflict-rule table | E4-2, E5-1 | Week 4 |
| Concierge swap-acceptance baseline | E7-3 gate calibration | Week 8 |
