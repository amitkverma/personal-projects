# SkinMatch PIVOT — Validation Experiments

**Date:** 23 July 2026
**Decisions the gate must produce:** (1) build / kill / pivot-back / redesign · (2) **market choice** (India vs global English)
**Principles:** behavior over opinions; skin-in-the-game; your own data.

---

## Cluster 1 — Extraction & Density Spike *(PF1–PF4, PB4; answers PG3 market choice)*

**Experiment 1a — Extraction quality eval**
- Sample 50 skincare videos (25 Indian creators, 25 global English) via YouTube API transcripts. Hand-label ground truth: every product reference with stance (**endorse / mention / criticize**) and sponsorship disclosure.
- Run LLM extraction; score against labels.
- Thresholds: 🟢 endorse-stance precision **≥90%** and recall **≥80%** · entity resolution to SKU **≥85%** (PF3) · disclosed-sponsorship detection **≥95%**; undisclosed sponsorship uses conservative **"no disclosure found"** framing, never "unsponsored" (PF2) · log cost-per-video (PB4).
- 🔴 Endorse-precision <80% → the graph poisons itself; pipeline needs redesign before any build.

**Experiment 1b — Content density audit (the market-selection instrument)**
- For 5 concerns (acne, pigmentation, dryness, aging, sensitivity) × 2 markets: count distinct creators recommending products in the last 18 months, and products endorsed by **≥3 independent** creators.
- Consensus viability per concern: 🟢 ≥15 independent endorsing creators AND ≥5 multi-endorsed products · 🔴 below half that → no consensus exists to aggregate in that market.
- Output: side-by-side market table → feeds the market decision with data, not debate.

**Effort:** ~1 week · **Cost:** API fees only

---

## Cluster 2 — Creator Posture *(PB2, PB3, PE3, PG2)*

**Experiment 2a — Legal posture review (desk)**
- YouTube API ToS (storage, derivative-use limits), fair use / fair dealing (US; India Copyright Act §52), publicity rights per market, FTC/ASCI rules relevant to sponsorship labeling.
- Output: red/yellow/green memo on what we may **store**, what we may **display** (quotes vs clips vs official embeds), and required sponsorship-label framing.
- 🔴 Red on display of names/quotes → concept requires opt-in redesign before build.

**Experiment 2b — Creator reaction outreach**
- 10 creators (5 Indian micro, 5 global mid-tier). Show a receipts-UI mockup **featuring their own content, attributed**. Record: hostile / neutral / positive; would they opt in to an official presence?
- **XYZ:** *At least 6 of 10 creators react neutral-or-positive, and ≥3 express interest in opting in.*
- 🔴 Majority hostile → the "creators as channel" assumption inverts to "creators as adversaries"; redesign posture (opt-in-first, rev-share) before build.

**Effort:** 2–3 days legal + 2 weeks outreach elapsed · **Cost:** ~₹15–30k if formal legal consult

---

## Cluster 3 — Consensus Value *(PV1, PV2, PV5, PS4; free reads on PG1)*

**Experiment 3a — Framing A/B content test (the PV1 kill-test)**
- 6 short-form pieces, same product story, three framings:
  (A) *"Creator X recommends…"* (parasocial baseline)
  (B) *"14 creators independently recommend…"* (consensus)
  (C) *"14 creators recommend — 11 with no sponsorship detected"* (honest consensus)
- **XYZ:** *Consensus framings (B/C) achieve ≥80% of the single-creator framing's click-through — parity proves aggregate trust exists; C beats B by ≥20% — sponsorship-discounting is felt, not insider.*
- 🔴 B/C collapse vs A → PV1 false: people trust *their* creator, not a number. Pivot-back signal.

**Experiment 3b — Landing page + commitment ladder**
- Two positioning variants (consensus-led vs "verified by ingredients"-led → PS4). Ladder: email → 3-question survey (geography, platform, current routine source) → **"paste a creator video you want turned into a routine for you"** (skin-in-the-game; seeds Cluster 4's concierge).
- Thresholds: 🟢 ≥15% visitor→waitlist · ≥25% waitlist→link submission. Signup geography feeds the market decision.

**Experiment 3c — Keyword research (desk, PG1)**
- Volume check on consensus-style queries per market ("best acne serum dermatologist recommended", "is X ad sponsored", "creator routine dupe").

**Effort:** page 1–2 days, content ~4 days, 2–3 weeks elapsed · **Cost:** ₹0–15k boost

---

## Cluster 4 — Routine Quality & Swaps *(PV4, PE1, PV3; observe PU1/PU2)*

**Experiment 4a — Derm panel on consensus routines**
- From Cluster 1 output (fallback: hand-mine 20 videos), generate 10 consensus routines (5 concerns × 2 budget levels). Two dermatologists rate each: safe / effective / would-recommend; flag harmful stacks.
- Thresholds: 🟢 ≥70% acceptable with at most minor edits · any "harmful" rating → documented as rules-engine requirements (PE1), not just noted.

**Experiment 4b — Concierge routines with the swap test**
- 20 waitlist users who submitted creator links: deliver a personalized consensus routine manually (WhatsApp/email). Where their budget is exceeded, show **creator's exact pick vs ingredient-matched cheaper swap, side by side**.
- Measure: swap acceptance, receipts tap-through (PU2), consensus-score trust reactions (PU1), affiliate-link CTR (feeds Cluster 5).
- **XYZ:** *At least 40% choose at least one swap when it saves ≥30%, and at least 50% click at least one buy link.*
- 🔴 Swap acceptance <15% → the pillar synthesis fails; influencer intent is SKU-literal, and the dupe engine belongs in the ingredient pillar only.

**Effort:** 4a 3–4 days + panel · 4b ~1.5 weeks rolling · **Cost:** ~₹5–10k derm fees + incentives

---

## Cluster 5 — Economics & Scope Reality *(PB1, PS3, PT1)*

**Experiment 5a — Unit economics model v2 (desk)**
- Per-market matrix: affiliate rates & AOV (US vs India), **creator-link conflict discount** (share of users transacting via creators' own links), pipeline cost-per-video from 1a extrapolated to catalog scale, scenarios: affiliate-only / premium tier / future creator rev-share.
- Threshold: 🟢 ≥1 credible break-even scenario per candidate market — else the market decision must weigh monetization, not just density.

**Experiment 5b — Live affiliate links** (piggyback on 3a content + 4b concierge) — real CTR and commission data.

**Experiment 5c — Scope & capacity review**
- After both spikes price the work: size the two foundations (INCI DB — audit carried from `04-experiments.md` — plus endorsement pipeline) against actual team skills (PT1).
- Output: an honest verdict — **both moats / sequence one first / buy-partner for data** (PS3).

**Effort:** 2–3 days desk + piggyback · **Cost:** ₹0

---

## Carried over from the original plan

The **INCI data audit** (`04-experiments.md`, experiment 1) runs unchanged in week 1 — it now also supplies entity-resolution ground truth (1a) and the swap engine's data (4b).

## Four-week schedule

| Week | Running |
|------|---------|
| **1** | 1a extraction eval + 1b density audit · 2a legal review · 2b outreach begins · 3b landing live · 3c keywords · INCI audit (carried) · 5a model started |
| **2** | 3a framing A/B content · 2b outreach continues · Cluster 1 wraps → **preliminary market signal** · 4a routines generated from spike data |
| **3** | 4a derm panel · 4b concierge begins · 5b affiliate links live |
| **4** | 4b completes · 5c scope review · synthesis → **decision gate** |

## Decision framework

**Decision 1 — build / kill / pivot-back / redesign:**

| Signal pattern | Call |
|----------------|------|
| Extraction ≥ thresholds · density viable in ≥1 market · legal 🟢/🟡 · creators ≥6/10 non-hostile · consensus framing ≥80% parity · waitlist ≥15% · derm acceptance ≥70% | **Build the pivoted concept** in the market the data picks |
| Consensus value fails (3a collapse) but ingredient-pillar signals healthy | **Pivot back** to ingredient-first as lead; keep creator attribution as a minor social-proof garnish |
| Legal 🔴 or majority-hostile creators | **Redesign** as opt-in creator platform (consent + rev-share) before any build |
| Extraction unfixably poor, or both pillars' demand fails | **Kill** |

**Decision 2 — market:** density table (1b) × signup geography (3b) × economics matrix (5a) → pick one beachhead; the plan records the runner-up as expansion, not a parallel launch.

**Total: ~₹40–75k + 4 weeks part-time. Still no product code — the only engineering is a throwaway extraction spike.**
