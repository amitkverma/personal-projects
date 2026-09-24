# SkinMatch — Idea Brainstorm (Initial Discovery)

**Date:** 23 July 2026
**Product stage:** New product, no prior validation
**Discovery goal:** Build/kill decision
**Target market:** India (Nykaa, Amazon.in, Flipkart, Purplle ecosystem)

## Market context used for ideation

- India's skincare market is shifting from "natural/herbal" marketing to ingredient-literate buying — the rise of Minimalist, The Derma Co, and Dot & Key proves demand for ingredient-first positioning.
- Global ingredient-analysis tools (INCIDecoder, Skinsort, CosDNA, Yuka) have **poor coverage of Indian D2C brands** and no Indian price data — a real gap.
- India has a strong "dupe culture" (affordable alternatives to imported actives) and extreme price sensitivity.
- Indian-skin-specific concerns (hyperpigmentation, PIH, tan, humidity-driven acne) are underserved by Western-centric tools.
- WhatsApp is the dominant sharing/communication channel; zero-install experiences matter for reach.

---

## Product Manager perspective (market fit, value, competitive advantage)

| # | Idea | Rationale |
|---|------|-----------|
| PM1 | **India Dupe Finder** — enter an expensive (often imported) product, get Indian-market alternatives ranked by ingredient-match % with ₹ savings shown | Most differentiated, most shareable value prop; monetizes via affiliate links; nothing does this for Indian brands/prices |
| PM2 | **Claim Checker** — compare front-of-pack marketing claims against the actual INCI list (e.g., "niacinamide serum" where niacinamide is 12th ingredient) | Builds trust and virality ("this product is lying to you" content writes itself) |
| PM3 | **Price tracking & alerts** across Nykaa/Amazon.in/Flipkart/Purplle for saved products | Clear affiliate revenue path; habitual re-engagement hook |
| PM4 | **Indian-skin concern mapping** — hyperpigmentation, PIH, tan, humidity acne on melanin-rich skin, mapped to evidence-backed ingredients and products | Western tools ignore this; strong content-SEO wedge |
| PM5 | **Derm-verified sensitivity presets** — fragrance-free, essential-oil-free, fungal-acne-safe lists reviewed by Indian dermatologists | Trust anchor; defensible via expert network |

## Product Designer perspective (UX, onboarding, engagement)

| # | Idea | Rationale |
|---|------|-----------|
| D1 | **Scan-the-shelf camera** — photograph an ingredient label in-store, get instant analysis via OCR | Magic moment; meets users at the point of purchase decision |
| D2 | **60-second Skin ID quiz** producing a shareable profile card (WhatsApp-ready) | Low-friction onboarding + built-in viral loop |
| D3 | **Personal traffic-light view** — every ingredient shown red/amber/green *relative to your profile*, not generic hazard scores | Personalization is the difference from static databases; answers "is this safe *for me*" |
| D4 | **Routine canvas** — visual AM/PM routine builder that flags ingredient conflicts (retinol + AHA) and totals routine cost | Makes the AI routine tangible and editable; budget angle fits India |
| D5 | **Two-depth content toggle** — "plain English" vs "enthusiast" (INCI names, concentrations, pH) on every screen | Serves beginners and enthusiasts without two products |

## Software Engineer perspective (technical innovation, integrations, platform)

| # | Idea | Rationale |
|---|------|-----------|
| E1 | **Ingredient-similarity engine** — set/vector similarity scoring over INCI lists; powers the dupe finder | The core IP; feasible with rule-based scoring before any ML |
| E2 | **Indian-brand ingredient database** — scraped + crowdsourced INCI lists for Indian D2C brands missing from global DBs | The data moat; hardest thing for a competitor to copy |
| E3 | **Price aggregation layer** — affiliate APIs/scrapers for Nykaa, Amazon.in, Flipkart with freshness guarantees | Table stakes for the price-comparison promise; affiliate revenue |
| E4 | **WhatsApp bot** — send a product link or label photo, get analysis back; zero-install | Distribution hack tailored to India; cheapest possible "app" |
| E5 | **Guard-railed AI routine builder** — LLM + RAG over the ingredient KB, constrained by a derm-reviewed rules engine (conflicts, pregnancy-safety, patch-test guidance) | Differentiates from generic ChatGPT advice via grounding and safety rails |

---

## Top 10 (prioritized for build/kill validation)

Weighted for: core value delivery, speed to validate, differentiation.

1. **India Dupe Finder** (PM1 + E1) — the sharpest, most testable value prop
2. **Personal traffic-light ingredient analysis** (D3 + PM5) — the "for me" safety promise
3. **Scan-the-shelf camera** (D1) — the magic-moment acquisition wedge
4. **WhatsApp bot** (E4) — zero-install distribution experiment
5. **Indian-brand ingredient database** (E2) — the moat everything else depends on
6. **Claim Checker** (PM2) — trust + viral content engine
7. **AI routine builder with conflict flags & budget cap** (E5 + D4)
8. **Skin ID quiz + shareable card** (D2)
9. **Price tracking & alerts** (PM3)
10. **Indian-skin concern mapping** (PM4)

## Ideas parked (still logged)

- Two-depth content toggle (D5) — good UX principle, not a validation-worthy bet on its own; fold into whichever ideas proceed.
