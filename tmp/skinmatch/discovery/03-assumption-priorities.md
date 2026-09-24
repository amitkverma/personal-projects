# SkinMatch — Assumption Prioritization (Impact × Risk)

**Date:** 23 July 2026
**Input:** 29 assumptions from `02-assumptions.md`
**Frame:** Build/kill discovery — priority goes to assumptions that, if false, mean *don't build*.

## The matrix

**Impact** = how much the build/kill decision changes if this assumption is false × how many users it affects.
**Risk** = (1 − confidence) × effort wasted if we build on it anyway.

### 🔴 High Impact × High Risk → TEST (leap-of-faith assumptions)

| Rank | ID(s) | Assumption (short) | Why it's leap-of-faith | Test effort |
|------|-------|--------------------|------------------------|-------------|
| **1** | **F1** | Full INCI lists are obtainable for most top-selling Indian products | If false, the foundation collapses and every bet degrades to a worse INCIDecoder. It's also the *cheapest* existential test — pure desk research | **Very low** (2–3 days) |
| **2** | **V1 + G2** | An ingredient-first buying segment exists in India **and** converts from content to a tool | If false: kill. The whole product presumes tool-seeking behavior beyond passive content consumption | **Low** (2 weeks) |
| **3** | **V2 + V3 + F2** | The dupe value chain holds: matches are expert-endorsable → users find match-% credible → users actually switch | The flagship differentiator stands on three unproven legs; any one failing breaks the bet | **Medium** (2–3 weeks) |
| **4** | **B1 + B2** | Affiliate economics produce meaningful revenue, and steering users to *cheaper* products doesn't structurally undermine it | If false, this is a nonprofit; monetization pivots (premium, brand-neutral subscriptions) need to be known *before* build | **Very low** (desk model, 2–3 days) |
| **5** | **V4 + U1 + E1** | Sensitive-skin users know their triggers well enough for personalization to help rather than falsely reassure | Bet B's promise; highest *harm-if-wrong* of all assumptions | **Low** (10 interviews, 1–2 weeks) |
| 6 | V7 | Beginners will follow an AI-built routine over influencer advice | Gates Bet D; cheap concierge test piggybacks on the interviews above | Low |
| 7 | G5 + T2 | Influencers will partner; derms will advise affordably | Gates both credibility and the main growth channel | Low (outreach) |

### 🟡 High Impact × Lower Risk → PROCEED with monitoring

| ID(s) | Assumption | Action |
|-------|-----------|--------|
| G3 | Ingredient-literacy wave still rising | Market signals (Minimalist growth, search trends) support it — proceed |
| E4 | DPDP Act compliance is achievable | Standard engineering work — handle at build time |
| U4 | LLM can take "make it cheaper" edits | Well-established capability — verify post-build |
| S4 | Global players won't localize to India first | Monitor their releases quarterly; speed is the mitigation |

### ⚪ Lower Impact × High Risk → DEFER (test later or descope)

| ID(s) | Assumption | Why defer |
|-------|-----------|-----------|
| U2 | OCR works on real Indian labels | Scan camera is an acquisition feature, not the core value; spike it only if Bets A/B validate |
| F3, B4 | Price-scraper reliability and legality | Matters at Step-2 rollout, not for the kill decision; do a light ToS review only |
| B5, E3 | Claim Checker legal exposure | Only if Bet C survives idea-level validation; needs legal opinion before launch, not before testing |
| F5 | Crowdsourcing fills DB gaps | Meaningless without an audience; revisit post-launch |
| V8 | Users return between purchase cycles | Untestable pre-MVP; design re-engagement hooks and measure post-launch |
| F4, E2 | AI guardrails prevent harmful advice | Bet D is Step-3 in the rollout; red-team when building it |
| V5, V6, U3, G1, G4 | Scan behavior, claim-check virality, beginner comprehension, channel reach, web-first | Each gets partially answered *for free* inside the Rank 1–5 experiments |

### ⚫ Strategy & Team → DECIDE, don't experiment

- **S1/S2/S3** (incumbent response, DB moat, India beachhead): informed by F1 and the demand test results; revisit at the decision gate.
- **T1/T3** (skills coverage, runway): founder decisions. Do an honest skills-vs-MVP inventory alongside the experiments.

---

## Test-together clusters

1. **Data Foundation Audit** → F1 (+ informs B3, S2)
2. **Demand & Conversion Funnel** → V1, G2 (+ reads on G1, G4, V6 for free)
3. **Dupe Value Chain** → F2 first (experts), then V2/V3 (users) — sequenced, because there's no point testing user switching on dupes experts would reject
4. **Economics Desk Model** → B1, B2
5. **Sensitive-Skin Interviews** → V4, U1, E1 (+ V7 concierge add-on)

## Suggested sequence logic

- Clusters **1** and **4** are desk work — run both in week 1; either can kill cheaply.
- Cluster **2** starts in week 1 (content takes time to accumulate signal).
- Cluster **3** waits for Cluster 1 output (need real INCI data to generate dupe pairs).
- Cluster **5** runs in parallel from week 2.
