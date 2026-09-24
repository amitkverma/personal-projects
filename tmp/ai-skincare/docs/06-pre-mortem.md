# Pre-Mortem: Dupe Twin MVP (PRD v2)

**Date:** 2026-07-24 · **Status:** Draft
**Scenario:** It's November 2026. The MVP launched to 200 waitlist users and failed — swap acceptance under 15%, D7 under 10%, zero organic sharing, founder exhausted. Working backward: what killed it?
**Framework:** Tigers (real risks) / Paper Tigers (scary but manageable) / Elephants (what we're not saying out loud).

---

## Risk Summary

- **Tigers: 11** (4 launch-blocking, 4 fast-follow, 3 track)
- **Paper Tigers: 5**
- **Elephants: 4**

---

## Launch-Blocking Tigers

| # | Risk | Likelihood | Impact | Mitigation | Owner | Deadline |
|---|---|---|---|---|---|---|
| T1 | **DPDP/consent exposure.** Face capture is personal data under India's DPDP Act 2023, and everyone under 18 is a "child" requiring verifiable parental consent — while skincare content skews young. Penalties run to ₹250 Cr for serious violations; unlike BIPA there are no per-scan statutory damages, but a Data Protection Board complaint + press cycle would poison trust in the exact community we need. | Medium | Critical | Legal review already flagged as blocker — add teeth: DPDP-compliant notice + consent flow, hard 18+ age gate, immediate raw-image deletion with logs, DPA with the scan vendor + confirm processing location/cross-border basis, grievance contact per IT Rules; counsel review before first invite | Amit | Before first invite |
| T2 | **Camera capture dies in Instagram/YouTube in-app browsers** — exactly where 100% of beachhead traffic lands. First-session wow becomes first-session error screen; scan completion craters and the funnel dies at step 1. | High | Critical | Week-2 spike: test vendor SDK in Instagram/YouTube webviews on Android (the ~95% majority) + iOS *before* signing the vendor contract; build the "open in browser" hand-off as a first-class designed flow with its own completion metric, not an error fallback | Amit | Week 2, pre-contract |
| T3 | **Scope vs. capacity.** The v2 MVP is four subsystems (scan, dupe engine + DB, routine, journal) in 10 weeks, solo, *while also* producing 3 Reels/Shorts a week and running the concierge. The most likely failure mode isn't any single risk — it's shipping all four at 60% quality in week 14. | High | Critical | Pre-commit a **descope ladder now**, while calm: cut in order (1) streaks/insights P1s → (2) journal photos (keep ratings/tags) → (3) routine receipt → (4) reminders to email-only. Scan, dupe engine, and basic check-in are never cut. If week 6 milestone slips >5 days, execute the ladder — no renegotiation | Amit | Ladder written this week; trigger at week 6 |
| T4 | **Scan vendor economics/access.** Haut.AI and Perfect Corp sell B2B — enterprise minimums, annual contracts, or USD per-scan pricing that makes a free consumer tier impossible at Indian ARPU; or no browser SDK at all. | Medium | Critical | Get real pricing + SDK docs from both in week 1 (not week 2); identify a fallback tier-2 vendor; define walk-away math (blended cost must stay <₹5/scan, ~$0.06, at free tier — Indian revenue per user leaves no slack for Western per-scan rates) before negotiating | Amit | Week 2 |

## Fast-Follow Tigers

| # | Risk | Likelihood | Impact | Planned Response | Owner |
|---|---|---|---|---|---|
| T5 | **Database coverage gap.** 500 seeded products vs. a beachhead that chases weekly viral launches and Nykaa sale cycles — early users search, hit "not indexed," screenshot the miss, and leave. The 85% lookup-success target may be unreachable at 500 SKUs, especially across Indian D2C + K-beauty + prestige. | High | High | Seed selection driven by concierge-phase demand data + Reels trend monitoring + Nykaa bestsellers, not editorial guess; daily hot-add triage of "notify me" logs in launch weeks; treat lookup-success as the week-1 dashboard number | Amit |
| T6 | **Journal habit doesn't form.** Health-app D7 reality is often <10%; our 25% target is aggressive. India's Android dominance helps (Chrome web push is reliable for the majority), but iOS users need email, Indian email open rates are poor, and the channel users actually check — WhatsApp — costs per message via the Business API. | Medium | High | Reminder channel decided by week 4 (web push primary for Android, email fallback); make check-in ≤20s a hard requirement with usability tests; if week-2 cohort check-ins <20%, interview 10 lapsed users before adding any gamification; evaluate WhatsApp Business API economics post-MVP | Amit |
| T7 | **Scan output disappoints or offends.** "11 conditions detected" reads as clinical judgment; and models under-trained on Indian skin tones (Fitzpatrick IV–VI — essentially our entire user base) will mis-read pigmentation and acne, producing wrong or harsh results users will post about — in our own acquisition channel. | Medium | High | Indian-skin-tone accuracy audit before vendor pick (already gated); soften result language ("what we noticed" not diagnoses); show confidence levels; in-product feedback flag on scan results with human review of every flag in launch cohort | Amit |
| T8 | **Swap fear wins.** Users love the receipts but don't switch — browsing pleasure, buying anxiety (V2). Acceptance lands at 15–20%: not failure, not validation. | Medium | High | Concierge baseline *before* launch calibrates the bar; ship patch-test framing + "start with your cheapest category" nudges (moisturizer, cleanser — low-risk swaps) before pushing treatment swaps | Amit |

## Track Tigers (monitor, don't delay)

- **T9 — An incumbent moves first.** SkinSort ships personalization (has the database and community), Nykaa/Tira white-labels a skin analyzer in-app (has distribution and purchase data — but its own-brand and seller conflicts are our neutrality wedge), or Cureskin opens to third-party recommendations (has Indian scan scale — but its kit economics resist it). We have a 12–18 month window. *Trigger:* any such release → accelerate scan+journal moat messaging. Check monthly.
- **T10 — Dupe culture crests.** *Trigger:* two consecutive quarters of declining India "skincare dupe" search trend / Reels hashtag velocity → shift messaging from "dupes" to "smart routine cost."
- **T11 — Price-data rot.** Scraper breakage silently shows stale prices → trust damage. *Trigger:* staleness >7 days on >10% of catalog → pager-level fix.

---

## Paper Tigers (scary, but manageable)

1. **"Brands/retailers will sue or delist us."** Brandefy and Skinskool operate openly; comparison content is established practice, and Indian law permits factual, non-disparaging comparative claims. Indian FMCG incumbents do litigate disparagement, but factual INCI comparison with language discipline stays clear; the realistic vectors are ASCI complaints and affiliate-program ToS (checked in B2), not litigation. *Becomes real if:* we copy brand imagery or claim clinical equivalence — language discipline covers this.
2. **"Yuka enters our space."** Its no-affiliate independence doctrine structurally blocks the dupe-shopping model, and it has minimal India presence or Indian barcode coverage anyway.
3. **"Lóvi undercuts us on price."** Their paid-acquisition CAC requires ~$55 (≈₹4,600) subscriptions and they have no India presence; matching ₹499/yr breaks their model entirely. Their trust debt is our tailwind either way.
4. **"Chemists will shred the ingredient-matching methodology."** Only if we overclaim. With the disclaimer discipline (formulation match ≠ identical results), patch-test prompts, and a credentialed advisor's name on the methodology, critique becomes engagement. *Becomes real if:* we launch the methodology post before recruiting the advisor (see Elephant E3).
5. **"Someone will scrape/clone our dupe results."** At MVP there's nothing proprietary to steal yet; the moat is the accumulating swap-outcome data, which isn't visible in the UI.

---

## Elephants in the Room

**E1 — The v2 scope reversal traded diagnosability for ambition.** The original plan tested assumptions in sequence (quiz-wedge first, scan/routine/journal after swap-trust was proven). v2 tests *four* kill-shot assumptions in one launch. If the numbers disappoint, we won't know which subsystem failed — was it scan quality, dupe credibility, routine fit, or journal friction? *Conversation starter:* "If week-12 metrics are mixed, what's our plan to attribute failure? At minimum, per-subsystem funnel instrumentation is P0, and the concierge phase must run to give us a dupe-engine-only baseline."

**E2 — A solo founder is building a daily-habit consumer app.** Consumer habit products demand months of daily content creation, community management, and support alongside engineering — historically the thing solo technical founders drop first (T1 in the assumptions doc, now compounded by the bigger build). *Conversation starter:* "What does week 9 look like on the calendar, hour by hour? If the honest answer is 70 hours, which of content, support, or code is dropped — and should we line up a contractor or co-founder for it now?"

**E3 — We keep deferring the credibility hire.** The chemist advisor gates the methodology post, the scoring weights, and the explanation language — three launch-path items — yet it's an open question with no candidate list. Every week without it, E1-risk content ships unreviewed. *Conversation starter:* "Name three candidate advisors this week, or move the methodology post after launch."

**E4 — ₹499/yr may cap this as a lifestyle business.** At 3–5% conversion, the beachhead ceiling is ~₹1.5–5 Cr ARR — fine for indie, fatal for venture. Indian subscription willingness-to-pay is structurally low; organic-CAC failure makes paid acquisition impossible at this price, and the venture-scale path in India is probably commerce (affiliate → marketplace economics, the Nykaa gravity) rather than subscriptions — which tensions directly with the neutrality positioning. Nobody has said which outcome we're building for. *Conversation starter:* "Indie-profitable or venture-scale? The answer changes pricing, how long we tolerate free growth, whether monetization tilts subscription or commerce, and whether E2 gets solved with hiring."

---

## Go/No-Go Checklist (before first invite)

- [ ] T1: Legal sign-off on DPDP-compliant scan flow (consent copy, 18+ gate, deletion logs, vendor DPA + processing location); scan flag stays off if unresolved
- [ ] T2: Scan completion verified inside Instagram + YouTube webviews on Android and iOS, or hand-off flow tested with >70% completion
- [ ] T3: Descope ladder written and week-6 checkpoint honored
- [ ] T4: Vendor contract fits <₹5/scan blended; fallback vendor identified
- [ ] Scoring gate passed: ≥80% agreement on 50-pair ground truth (unchanged from PRD)
- [ ] Concierge baseline recorded (calibrates the 30% swap-acceptance bar)
- [ ] Per-subsystem funnel instrumentation live (E1)
- [ ] Chemist advisor named on methodology page (E3)
- [ ] Rollback plan: scan feature-flagged so launch can proceed quiz-only if T1/T2 slip at the last minute
- [ ] Support plan: founder inbox + FAQ; every scan-result complaint human-reviewed in launch cohort

**Verdict:** No launch-delaying showstoppers *if* T1–T4 are worked in weeks 1–2 as specified. The single highest-leverage insurance policy is the **scan feature flag** — it converts the two scariest tigers (DPDP compliance, webview capture) from launch-blockers into toggles, preserving the launch date no matter what legal or the SDK does.
