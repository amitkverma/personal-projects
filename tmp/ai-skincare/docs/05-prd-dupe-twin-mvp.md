# Product Requirements Document: Dupe Twin MVP

**Author:** Amit Verma
**Date:** 2026-07-24
**Status:** **v3 — Final, build-ready.** v2 scope (scan + routine + journal) hardened with pre-mortem mitigations (`docs/06`) and aligned to the product strategy (`docs/08`). Build backlog: `docs/07`.
**Context chain:** competitive landscape (`docs/01`) → lean canvas (`docs/02`) → assumptions (`docs/03`) → beachhead (`docs/04`) → this PRD → pre-mortem (`docs/06`) → backlog (`docs/07`) → strategy (`docs/08`).

---

## 1. Executive Summary

A web app for the Indian market with a complete daily loop: **scan your face → get your routine → fill it with the cheapest products that fit your skin → journal your skin daily and watch it improve.** The face scan is the viral acquisition hook; the personalized dupe engine over the Indian catalog is the differentiator; the routine + journal are the retention engine that makes this a daily-habit app rather than a one-shot lookup. Strategy north star: *verified ₹ saved per active user per month* — great skin shouldn't cost rich-person money.

## 2. Background & Context

Dupe finding today is generic and US-centric (SkinSort/Skinskool match formulas, not skin, and barely cover Indian brands or ₹ prices), personalized skincare apps are price-blind (Lóvi, SkinGenie), and India's scale player (Cureskin) only recommends its own kits. Our beachhead — Indian metro women 18–28 in Instagram/YouTube dupe culture spending ₹2,000+/mo — manually triangulates SkinSort, INCIDecoder, Reddit, and Reels comments to answer one question: *"Will the cheap one work for me?"* Full analysis in `docs/01`.

**Scope rationale (v2 decision, confirmed after pre-mortem):**
- **Scan** drives Reels/Shorts virality and first-session wow (Cureskin proves scan demand in India; Lóvi globally). Pre-mortem consequence accepted and mitigated: the scan is **feature-flagged** so legal or SDK trouble degrades the launch to quiz-only instead of delaying it.
- **Routine + daily journal** convert a lookup utility into a daily habit (health-app adherence loop), directly mitigating retention risk V3.
- The **quiz remains** — scan can't see allergies, sensitivities, or budget. Scan (objective) + quiz (subjective) merge into one skin profile; the profile must be complete from quiz alone (flag-off architecture).

**Strategy constraints this PRD inherits (`docs/08` trade-offs):** explainable deterministic matching (no black-box claims), no sponsored placement ever, depth on ~500 high-demand India-relevant products over bulk coverage, web-first, India-only, skincare-only.

## 3. Objectives & Success Metrics

**Goals**
1. Validate personalized dupes get accepted: ≥30% of shown swaps marked "I'd buy this" or clicked out to retailer (bar calibrated by concierge baseline).
2. Validate the daily loop: ≥40% of activated users log ≥3 journal check-ins in their first week; D7 retention ≥25%.
3. Validate organic shareability: ≥10% of users share/download a receipt or scan result.
4. Validate scoring credibility: ≥80% agreement with community-consensus dupes on a 50-pair ground-truth set (offline, pre-launch — hard gate).

**Non-Goals (explicitly out of scope)**
1. Monetization (subscription or affiliate revenue) — instrument outbound clicks, charge no one yet.
2. Native app — web-first; native only after the week-12 gate.
3. AI chat assistant — post-MVP.
4. Reverse lookup ("cheapest product for my concern," no anchor product) — post-MVP.
5. Haircare/body care, retailers outside India, vernacular localization, men's marketing, medical skin conditions — per strategy trade-offs.
6. Bulk database coverage — 500 curated SKUs + same-day hot-add beats 60k stale entries at MVP.

**Success Metrics**
| Metric | Current | Target | Measurement |
|---|---|---|---|
| Swap acceptance rate | concierge baseline TBD | ≥30% | "I'd buy this" tap or retailer click-out / dupe results shown |
| Journal habit formation | — | ≥40% log 3+ check-ins in week 1 | check-in events / activated users |
| D7 / D30 retention | — | ≥25% / ≥15% | returning users by cohort |
| Monthly re-scan rate | — | ≥30% of M1 actives | re-scans / eligible users |
| Share rate (receipt or scan) | — | ≥10% | share/download events / artifacts generated |
| Scan completion | — | ≥70% | successful scans / scan starts (incl. webview hand-off) |
| Lookup success ("product found") | — | ≥85% | successful lookups / search attempts |
| Ground-truth scoring agreement | — | ≥80% | offline eval vs. 50 community-validated dupe pairs |

**Guardrails (pre-mortem):** scan-complaint rate (every complaint human-reviewed in launch cohort), price staleness <7 days on ≥90% of catalog, refund/cancel-complaint rate ("are we becoming Lóvi?" alarm — applies once monetization exists).

## 4. Target Users & Segments

Beachhead persona "Maya" (`docs/04`): Indian metro/tier-1 women 18–28, 3+ skincare creators followed on Instagram/YouTube, 4+ product routine at ₹2,000+/mo, has researched a dupe in the last 6 months. Segment ~800k–2M. Current workaround: manual SkinSort + INCIDecoder + Reddit triangulation (all US-centric, none with ₹ prices), plus ad-hoc camera-roll selfie comparisons for progress.

## 5. User Stories & Requirements

Full decomposition with effort/dependencies lives in `docs/07`; this section is the requirements source of truth.

**P0 — Must Have**

*Onboarding & profile*
| # | User Story | Acceptance Criteria |
|---|---|---|
| 1 | As Maya, I scan my face and see my skin analysis | **Behind a feature flag — app fully functional quiz-only when off.** In-browser capture with lighting/framing guidance; core conditions via licensed API validated on Indian skin tones; results <30s; counsel-approved DPDP-compliant consent screen before capture; 18+ age gate (DPDP treats under-18s as children requiring parental consent — we exclude them instead); **flag stays off until DPDP counsel review clears**; raw images deleted post-processing (deletion logged), only derived metrics stored; webview detection → designed "open in browser" hand-off with its own funnel event |
| 2 | As Maya, I complete a short quiz for what the scan can't see | ≤6 questions, ≤60s: sensitivities/allergens, concern priority, budget ceiling; scan + quiz merge into one versioned skin profile; **profile complete from quiz alone** |
| 3 | As Maya, my scan results feel observational, not diagnostic | "What we noticed" language with confidence levels — never diagnoses; "this looks wrong" flag on results, human-reviewed in launch cohort |

*Routine & dupes (the differentiator)*
| # | User Story | Acceptance Criteria |
|---|---|---|
| 4 | As Maya, I get an AM/PM routine for my profile | Rule-based generation: steps + product slots pre-filled by fit+price engine at my budget; conflict rules (retinoid+AHA etc.) chemist-reviewed; editable (swap/remove/add/"already own"); routine total cost shown |
| 5 | As Maya, I search any popular product and find its cheap twin for my skin | Search-as-you-type over ≥500 seeded India-relevant products (seed list driven by concierge demand + Reels trend data + Nykaa bestsellers, not editorial guess); top 1–3 dupes ranked by fit×price with ₹ price, price-per-ml, % match, personal-fit flags; "not yet indexed — notify me" logs demand |
| 6 | As Maya, I understand *why* a swap is safe | Explanation card: shared key actives, notable differences, allergen warnings from my profile; plain language; patch-test prompt on every swap; persistent "formulation match ≠ guaranteed identical results" disclaimer; all copy chemist-advisor-approved |
| 7 | As Maya, I get a shareable savings receipt | Single-swap receipt (original vs. twin, ₹ saved, match %) as one-tap download/share image; WhatsApp share intent first-class |

*Daily loop (the retention engine)*
| # | User Story | Acceptance Criteria |
|---|---|---|
| 8 | As Maya, I check off my routine daily | AM/PM checklists from my routine; one-tap complete; streak counter; IST day boundaries |
| 9 | As Maya, I journal my skin like a health app | Daily check-in ≤20s (usability-tested): skin-feel rating 1–5, optional tags, optional note + photo; photos private, deletable, outside the biometric pipeline |
| 10 | As Maya, I see my progress over time | Timeline of check-ins + scans; monthly re-scan side-by-side comparison (flag-dependent); swap-outcome callouts ("redness improved since switching to [dupe]") only with ≥2 scans + adherence data, observational language |
| 11 | As Maya, I get a gentle daily reminder | Web push (default — India is ~95% Android, where Chrome web push is reliable) with email fallback for iOS; AM/PM timing controls; one-tap disable; no guilt copy, no dark patterns |

*Founder/ops & diagnosability*
| # | User Story | Acceptance Criteria |
|---|---|---|
| 12 | As the founder, I can diagnose a mixed result | **Per-subsystem funnel instrumentation (pre-mortem E1):** onboarding, engine (search→results→accept→click-out), routine (generate→edit→check-off), journal (check-in→streak→re-scan), sharing — each independently measurable on one dashboard vs. targets; no PII beyond email, no raw images in analytics |
| 13 | As the founder, I can hot-add trending products in <15 min | Admin path: INCI + prices → live same-day; validation + match preview + audit log |

**P1 — Should Have** *(first candidates on the descope ladder)*
| # | User Story | Acceptance Criteria |
|---|---|---|
| 14 | Routine-level receipt ("₹12,000 → ₹3,500") | Full-routine original vs. optimized totals as shareable image — descope cut #3 if week 6 slips |
| 15 | Bad-dupe feedback | "Didn't work for me" + reason; joined to profile+swap data (flywheel seed) |
| 16 | Current prices | Refresh job; staleness ≤7 days shown; alert at >10% catalog stale; per-retailer failure isolation |
| 17 | Streaks & milestones | Badges, "4 weeks consistent," shareable progress card; never shames a broken streak — descope cut #1 |
| 18 | Journal insights | Heuristic correlations ("breakout tags rose the week you added X"), labeled observation not diagnosis |

**P2 — Nice to Have / Future**
| # | User Story | Acceptance Criteria |
|---|---|---|
| 19 | Reverse lookup (concern → cheapest fitting product) | Post-MVP |
| 20 | AI chat assistant | Post-MVP |
| 21 | Native iOS/Android | After week-12 gate |

## 6. Solution Overview

- **Web app**, mobile-first responsive, Android-first QA (India is ~95% Android); Instagram/YouTube in-app webviews are a first-class target (full-funnel QA there; scan hand-off flow designed, not an error fallback); performance budgeted for mid-range Android on 4G.
- **Scan:** licensed API (Haut.AI / Perfect Corp class) — buy, don't build. **Vendor selection gated on week-1 spike:** webview SDK behavior + real pricing (walk-away: <₹5/scan blended, ~$0.06 — Indian ARPU leaves no slack) + accuracy audit on Indian skin tones (Fitzpatrick IV–VI — our entire market, not an edge case). Fallback vendor identified before contract.
- **Fit+price engine v0:** deterministic, explainable ingredient-similarity scoring (weighted actives, INCI-order-aware, synonym-normalized) × profile filters (hard allergen exclusions) × price-per-use. Built as a pure library with an eval harness; **≥80% ground-truth agreement gates all UI work.**
- **Routine generation v0:** rule-based templates filled by the engine. No ML; explainability is the trust story (strategy trade-off).
- **Data:** seed ~500 India-relevant products (INCI + MRP + ≥2 retailer selling prices each across Nykaa/Amazon.in/Flipkart/Purplle); hot-add path over bulk coverage; seed list from concierge demand + Reels trend data + Nykaa bestsellers.
- **Auth:** email magic link; waitlist imported as pre-authorized invites.
- **Compliance posture:** DPDP-compliant consent-first capture, immediate raw-image deletion with logs, 18+ gate (DPDP parental-consent avoidance), vendor DPA + processing-location check, grievance-redressal contact per IT Rules, DPDP legal review as **launch blocker** — with the feature flag as the pressure valve that protects the launch date.
- **Rollback plan:** scan flag off + invite batches pausable at any point.

## 7. Open Questions

| Question | Owner | Deadline |
|---|---|---|
| Scan vendor choice: webview behavior, per-scan price, Indian-skin-tone accuracy audit (SPIKE-1) | Amit | Week 2, pre-contract |
| Counsel-approved DPDP consent copy + compliance review (consent, deletion, vendor DPA, cross-border processing) — blocking scan-flag-on, not launch | Amit | Week 8 |
| Legal read on scraping/attributing Indian retailer prices + INCI lists (SPIKE-2) | Amit | Before build starts |
| Chemist/derm advisor recruited: disclaimer copy, scoring weights, conflict-rule table | Amit | Week 4 (blocks stories 4, 6) |
| Concierge baseline: swap-acceptance rate of hand-picked dupes (calibrates the 30% bar) | Amit | Week 8 |
| Reminder channel: web push covers the Android majority; is email fallback enough for iOS at launch? WhatsApp Business API cost — post-MVP? | Amit | Week 4 |
| Affiliate ToS compatibility — Amazon Associates India, Flipkart Affiliate, Cuelinks/EarnKaro for Nykaa/Purplle (informs future monetization; non-blocking) | Amit | During build |

## 8. Timeline & Phasing

~10 weeks to private launch. Concierge/content validation from `docs/04` runs in parallel throughout.

- **Week 1:** SPIKE-1 (vendor webview + pricing + Indian-skin-tone audit) and SPIKE-2 (data legal + 50-pair ground-truth set + DPDP counsel kickoff). Engine build starts.
- **Week 1–2:** Engine v0 + eval harness → **Gate 1: ≥80% ground-truth agreement or all UI work pauses.**
- **Week 2–4:** Seed database + hot-add admin; auth + quiz + scan integration (flagged) + merged profile.
- **Week 4–6:** Routine generation/editing/check-offs; dupe lookup + explanation cards + single-swap receipt. **Week-6 checkpoint: if >5 days behind, execute descope ladder** (streaks → journal photos → routine receipt → push-to-email-only). Engine, lookup, basic check-in, analytics are never cut.
- **Week 6–8:** Journal, timeline, reminders, P1s if on schedule.
- **Week 8–10:** Analytics dashboard + taxonomy audit; webview/device QA; **Gate 2: `docs/06` go/no-go checklist** (legal sign-off or flag-off launch, vendor economics, concierge baseline, advisor named, rollback tested). Invites in batches (50/50/100) with daily metric review.
- **Week 12 — Gate 3:** swap acceptance ≥30%, week-1 journal habit ≥40%, D7 ≥25%, share ≥10% → green-light monetization + native track. Mixed result → per-subsystem funnels (story 12) attribute the failure; interview 10 rejectors/churned before writing more code.

---

*Companion docs: risk register & go/no-go checklist in `docs/06`; build backlog in `docs/07`; strategy & trade-offs in `docs/08`.*
