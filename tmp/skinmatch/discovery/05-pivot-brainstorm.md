# SkinMatch PIVOT — Idea Brainstorm (Influencer-Consensus + Ingredient Pillars)

**Date:** 23 July 2026
**Pivot:** AI routine builder grounded in **aggregated influencer consensus** (mined from creator content, with attribution as social proof), running alongside the original **ingredient-first discovery** pillar as equals.
**Positioning hypothesis:** *"What influencers recommend, verified by what's inside."*
**Open again:** market (India vs global English) and build/kill.

## Market context used for ideation

- Skincare buying decisions today largely start on creator content (YouTube derms, Instagram/TikTok skinfluencers) — the pivot meets demand where it already forms instead of fighting it.
- Existing players monetize the *creator side* (LTK, ShopMy, Wishlink storefronts) or the *community side* (Picky, review apps). Nobody aggregates **cross-creator consensus** and stress-tests it against **ingredients** — that seam is open.
- The dirty secret of the space: a large share of influencer "recommendations" are paid. Consensus mining that can't tell sponsored from organic aggregates astroturf. Solving that is both the hardest problem and the sharpest differentiator.
- Creator-content mining has a legality gradient: YouTube transcripts via official APIs ≫ Instagram scraping (ToS-hostile). Attribution ("14 creators recommend, here are the clips") doubles as social proof and a defensible fair-use posture.

---

## Product Manager perspective

| # | Idea | Rationale |
|---|------|-----------|
| PM1 | **Creator Consensus Score** — per product/concern: how many *independent* creators endorse it, **discounting sponsored content** ("14 creators recommend — 11 unsponsored") | The core promise made honest; the anti-astroturf filter is the moat nobody else wants to build because it bites the hand that feeds the industry |
| PM2 | **"Influencer routine, your budget"** — consensus routine for your concern, products auto-swapped with ingredient-matched dupes to hit your budget | The two pillars literally compose; nobody else can do this without both databases |
| PM3 | **Ingredient-verified endorsements** — every influencer pick cross-checked against your sensitivities ("loved by creators, but contains the fragrance you avoid") | The positioning in one feature: trust the crowd, verify the label |
| PM4 | **Trend radar** — what's rising in creator content this month, with an ingredient reality-check on each trend | Retention hook + endless SEO/PR content |
| PM5 | **Credibility tiers** — dermatologists vs estheticians vs general creators, transparently weighted; "derm-only consensus" filter | Turns "influencer suggestions" from a liability into a spectrum users control |

## Product Designer perspective

| # | Idea | Rationale |
|---|------|-----------|
| D1 | **Routine-from-a-link onboarding** — paste a reel/video you liked; app extracts the routine and personalizes it | Meets users at the exact moment of influencer-inspired intent; magic-moment onboarding |
| D2 | **Consensus-vs-You view** — side by side: what creators recommend for skin like yours vs flags for *your* sensitivities | The trust-but-verify UI; makes the dual-pillar value visible on one screen |
| D3 | **Receipts on every claim** — tap "recommended by 14 creators" → actual clips/quotes with timestamps | Attribution as credibility; also the defensible-use posture for creator content |
| D4 | **Budget slider on routines** — drag the price; dupe engine swaps products in real time | Tangible, demo-able, deeply shareable |
| D5 | **Skin-twin proof** — "creators and users with skin like yours rate this 4.6" | Community flywheel for later; not a launch feature |

## Software Engineer perspective

| # | Idea | Rationale |
|---|------|-----------|
| E1 | **Creator-content mining pipeline** — YouTube transcripts + LLM extraction of product mentions, sentiment, and routine steps → structured endorsement DB | The pivot's foundation; YouTube-first keeps it on the safest ToS ground |
| E2 | **Sponsorship classifier** — detect disclosed (#ad, "sponsored") and undisclosed (coupon codes, brand-trip patterns) promotion to weight consensus | Powers PM1; genuinely hard, genuinely defensible |
| E3 | **Product entity resolution** — map "the Ordinary niacinamide" (spoken, misspelled, nicknamed) to catalog SKUs + INCI lists | Unsexy and mission-critical; links pillar 2 to pillar 1 |
| E4 | **Endorsement knowledge graph** — product ↔ creator ↔ concern ↔ ingredient; powers consensus, attribution, trends | The compounding data asset (replaces the INCI DB as *the* moat — now there are two) |
| E5 | **Freshness/decay model** — endorsements age out; creators change routines; reformulations tracked via INCI diffs | Prevents the DB from quietly rotting; a silent-killer risk if skipped |

---

## Top 10 (prioritized for build/kill validation)

1. **Creator Consensus Score with sponsorship discounting** (PM1 + E2) — the honest version of the core promise
2. **"Influencer routine, your budget"** (PM2 + D4) — the pillar synthesis and demo centerpiece
3. **Ingredient-verified endorsements / Consensus-vs-You** (PM3 + D2) — the positioning as a feature
4. **Receipts UI** (D3) — attribution, credibility, and legal posture in one
5. **Content mining pipeline** (E1) — foundation #1
6. **Product entity resolution** (E3) — foundation #2, links the pillars
7. **Credibility tiers / derm-only filter** (PM5)
8. **Routine-from-a-link onboarding** (D1)
9. **Trend radar** (PM4)
10. **Endorsement knowledge graph** (E4)

## Parked

- Skin-twin community proof (D5) — needs an audience first
- Freshness/decay model (E5) — build-phase concern, logged as a feasibility assumption
