# Discovery Plan: SkinMatch (Pivoted)

**Date:** 23 July 2026 *(v2 — supersedes the ingredient-first-only plan of earlier today)*
**Product stage:** New product (initial discovery — no validated demand)
**Concept:** Two equal pillars — **(1) ingredient-first discovery** (search, sensitivity filters, dupe finder, ingredient education) and **(2) AI routine builder from aggregated influencer consensus**, with sponsorship-discounted consensus scores and creator attribution ("receipts") as social proof.
**Positioning hypothesis:** *"What influencers recommend, verified by what's inside."*
**Discovery questions:** Should this be built at all? And **which market first** — India or global English?
**Decisions this informs:** Build / kill / pivot-back / redesign, **and** market selection
**Budget:** ~₹40–75k + ~4 weeks part-time; no product code (one throwaway extraction spike)

Supporting documents — original concept: [`discovery/01-ideas-brainstorm.md`](discovery/01-ideas-brainstorm.md) · [`02-assumptions.md`](discovery/02-assumptions.md) · [`03-assumption-priorities.md`](discovery/03-assumption-priorities.md) · [`04-experiments.md`](discovery/04-experiments.md) — pivot: [`05-pivot-brainstorm.md`](discovery/05-pivot-brainstorm.md) · [`06-pivot-assumptions.md`](discovery/06-pivot-assumptions.md) · [`07-pivot-priorities.md`](discovery/07-pivot-priorities.md) · [`08-pivot-experiments.md`](discovery/08-pivot-experiments.md)

---

## Ideas Explored

Two brainstorm rounds (15 ideas each, PM/Designer/Engineer perspectives). Round 1: ingredient-first concept (`01`). Round 2: influencer-consensus pivot (`05`). Carried into validation from round 2: Creator Consensus Score with sponsorship discounting, budget-swap consensus routines, Receipts UI, Trend radar, and all three foundations (mining pipeline, entity resolution, endorsement graph).

## Selected Ideas for Validation

| Group | Ideas | The promise |
|-------|-------|-------------|
| **Bet A — Consensus routines** (core) | Consensus Score + "influencer routine, your budget" (dupe-engine swaps) | "The routine creators actually agree on — at your price" |
| **Bet B — Trust & engagement** | Receipts UI + Trend radar | "Tap the number, see the actual clips" |
| **Foundation** | YouTube-first mining pipeline · product entity resolution · endorsement knowledge graph | The second data moat, alongside the INCI database |
| **Ingredient pillar** (parallel) | Search, sensitivity filters, dupe finder, education | Carried from v1; assumptions in `02`/`03` still stand |

## Critical Assumptions (pivot leap-of-faith set)

| # | Assumption | Category | Impact | Uncertainty | Priority |
|---|-----------|----------|--------|-------------|----------|
| PF1–PF4 | Extraction separates endorse/mention/criticize; sponsorship detectable; entities resolvable; enough content density per market to form consensus | Feasibility | Existential (+ decides market) | Medium-High | **P0** |
| PB2, PB3, PE3 | Creator content is legally usable and creators won't revolt; the ethical posture holds | Viability / Ethics | Existential | High | **P0** |
| PV1, PV2, PV5 | Aggregated consensus beats single-creator parasocial trust; sponsorship-discounting is felt; aggregation beats "just watch YouTube" | Value | Existential | High | **P1** |
| PV4, PE1, PV3 | Consensus routines are derm-quality; users accept budget swaps in creator-derived routines | Value / Ethics | High (the differentiator) | High | **P1** |
| PB1, PS3, PT1 | Affiliate revenue survives the creator-link conflict; one small team can dig two moats | Viability / Strategy / Team | High | Medium-High | **P1** |
| F1 (carried) | Full INCI lists obtainable for top products | Feasibility | Existential for pillar 1 | Medium | **P0** (runs week 1) |

Full maps: 24 pivot assumptions in `06`, 29 original in `02`. Deferred: retention (PV6/V8), freshness (PF5), moat compounding (PS1).

## Validation Experiments

| # | Tests | Method | Success criteria | Effort | Timeline |
|---|-------|--------|-----------------|--------|----------|
| 1a | PF1–PF3, PB4 | Extraction eval: 50 hand-labeled videos, both markets | Endorse precision ≥90%, recall ≥80%; entity resolution ≥85%; "no disclosure found" framing | ~1 wk | Week 1–2 |
| 1b | PF4 → PG3 | Content-density audit: 5 concerns × 2 markets | ≥15 independent creators & ≥5 multi-endorsed products per concern | (in 1a) | Week 1–2 |
| 2a | PB2 | Legal posture review (ToS, fair use/dealing, publicity rights) | 🟢/🟡 memo on store/display/labeling | 2–3 d | Week 1 |
| 2b | PB3, PE3, PG2 | Creator outreach: 10 creators shown receipts mockup of their content | ≥6/10 neutral-or-positive; ≥3 opt-in interest | 2 wks | Weeks 1–2 |
| 3a | PV1, PV2 | Framing A/B: single-creator vs consensus vs honest-consensus content | B/C ≥80% of A's CTR; C ≥ B+20% | ~4 d | Week 2 |
| 3b | PV5, PS4, PG3 | Landing page, 2 positioning variants, commitment ladder ending in creator-link submission | ≥15% visitor→waitlist; ≥25% waitlist→link submitted | 1–2 d | Weeks 1–4 |
| 4a | PV4, PE1 | Derm panel rates 10 consensus routines | ≥70% acceptable; harms → rules-engine requirements | 3–4 d | Week 3 |
| 4b | PV3, PU1, PU2 | Concierge routines for 20 users with side-by-side swap offers | ≥40% take a swap at ≥30% savings; ≥50% click a buy link | 1.5 wk | Weeks 3–4 |
| 5a | PB1, PS3 | Unit-economics matrix: market × monetization, incl. creator-link conflict + pipeline cost | ≥1 break-even scenario per market | 2–3 d | Week 1 |
| 5b | PB1 | Live affiliate links in 3a + 4b | Real CTR/commission data | 0.5 d | Weeks 2–4 |
| 5c | PS3, PT1 | Scope & capacity review after spikes | Verdict: both moats / sequence / buy data | 1 d | Week 4 |
| — | F1 (carried) | INCI audit of top 100 products (`04`, exp 1) | ≥70% coverage | 2–3 d | Week 1 |

## Discovery Timeline

- **Week 1:** extraction spike + density audit start · legal review · creator outreach begins · landing page live · keyword research · INCI audit · economics model
- **Week 2:** framing A/B content · outreach continues · spike wraps → **preliminary market signal** · consensus routines generated
- **Week 3:** derm panel · concierge begins · live affiliate links
- **Week 4:** concierge completes · scope review · synthesis → **decision gate**

## Decision Framework

**Decision 1 — build/kill/pivot-back/redesign:**

- **Build the pivoted concept** if: extraction meets thresholds, density viable in ≥1 market, legal 🟢/🟡, creators ≥6/10 non-hostile, consensus framing holds ≥80% parity, waitlist ≥15%, derm acceptance ≥70%.
- **Pivot back to ingredient-first lead** if consensus value fails (3a collapse — parasocial trust doesn't aggregate) while ingredient-pillar signals stay healthy.
- **Redesign as opt-in creator platform** (consent + rev-share) if legal comes back 🔴 or creators are majority-hostile.
- **Kill** if extraction is unfixably poor or demand fails across both pillars.

**Decision 2 — market:** density table (1b) × signup geography (3b) × economics matrix (5a) → one beachhead; runner-up logged as expansion.

## Structural risks to keep visible

1. **The data source is the adversary** — the product mines creators' content and intercepts their affiliate economics, then needs their goodwill as a channel. The posture (attribution-forward, opt-out honored, rev-share later) is a design input, not an afterthought.
2. **Two moats, one team** — the pivot doubled the foundations (INCI DB + endorsement graph). Week 4's scope review must answer this honestly.
3. **Honest labeling** — "unsponsored" claims that are wrong are a defamation and trust hazard; ship "no disclosure found" framing only.

---

*Living document — update experiment rows as results land; record gate decisions below.*

## Decision Log

| Date | Decision | Evidence |
|------|----------|----------|
| 23 Jul 2026 | Committed to full production build of ingredient-first concept (founder call) | Superseded same day by pivot |
| 23 Jul 2026 | **Pivoted** to influencer-consensus + ingredient dual-pillar concept; **build commitment and market choice reopened** — discovery reframed to build/kill + market selection | Founder decision; mechanic = aggregated consensus + social-proof attribution; pillars equal |
| — | *experiment results pending* | — |
