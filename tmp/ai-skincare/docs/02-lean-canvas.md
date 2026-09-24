# Lean Canvas — "SkinSaver" (working name)

**Concept:** AI face-scan skin analysis + personalized routines + routine-level cheapest-alternative optimization.
**UVP in one line:** *The AI skincare advisor that saves you money.*
**Market:** India only — ₹ pricing, Indian retailers and catalog throughout.
**Date:** July 2026 · Status: hypothesis — every box is an assumption to test, not a fact.

---

## 1. Problem

1. **Personalized skincare advice is expensive, inaccessible, or conflicted.** Metro dermatologist consults run ₹800–2,000/visit (and derm access is thin outside metros); influencer/brand recommendations are commission-driven; India's biggest AI skin app (Cureskin) only ever recommends its own product kits; global apps like Lóvi charge ~$55 (≈₹4,600) and have burned users with subscription traps.
2. **Skincare is overpriced for what's in the bottle.** Users routinely pay 3–10× for marketing, not formulation — imported prestige adds duty and distributor markups on top — but can't tell which cheap product is a true substitute *for their skin*. Indian D2C (Minimalist, The Derma Co, Dot & Key) has proven the same actives sell for ₹300–700.
3. **Dupe finding is generic, manual, and US-centric.** SkinSort/Skinskool match formulas, not skin — and their catalogs are thin on Indian brands, priced in $, with no Indian retailer links. Users must already know the expensive product, then cross-check ingredient lists themselves, with no guidance on whether the dupe suits their skin type, sensitivities, or current routine.

**Existing alternatives:** dermatologist visits, r/IndianSkincareAddicts + manual INCIDecoder research, generic US-centric dupe sites, Cureskin (own-brand funnel), Lóvi/SkinGenie (no India catalog, no real price optimization), Reels/Shorts dupe videos (unverified).

## 2. Solution

1. **AI skin scan → profile** (skin type, concerns, sensitivities). Buy-don't-build: license Haut.AI/Perfect Corp API for MVP rather than training a scanner.
2. **Fit + Price engine (the core IP):** ranks products by *(ingredient-level fit to your skin profile) × (price per use across Indian retailers — Nykaa, Amazon.in, Flipkart, Purplle)*. Works two ways: "find me the cheapest product for my concern" and "find a cheaper twin of this specific product."
3. **Routine Cost Optimizer:** builds your AM/PM routine, then shows "your routine: ₹12,000 → our version: ₹3,500 at 92% formulation fidelity" with per-swap explanations. The shareable, WhatsApp-forwardable artifact that drives growth.

## 3. Unique Value Proposition

**"Scan your face. Get your routine. Pay a third of the price."**
High-concept pitch: *Lóvi's brain + Skinskool's dupes + Yuka's honesty — for the Indian catalog.* Differentiation is the *intersection* — personalized fit AND price optimization AND transparent reasoning AND neutrality (we sell nothing of our own, unlike Cureskin) — not superiority on any single axis.

## 4. Unfair Advantage

Honest answer at day 0: **none** — the scanner is licensable, dupe algorithms exist. What compounds into one:
- **Data flywheel:** every scan + swap-acceptance + repurchase teaches the fit-price engine what actually works per skin profile — a dataset neither dupe sites (no skin data) nor analysis apps (no purchase data) possess.
- **Trust brand** in a category where the global leader burns users (Lóvi refund complaints) and the Indian leader is structurally conflicted (Cureskin recommends only its own kits) — cheap to earn now, expensive for incumbents to copy (Yuka can't take affiliate money; brands and own-brand apps can't recommend competitors' dupes).
- **Indian catalog depth:** a fresh database of Indian D2C + K-beauty-in-India + prestige with ₹ prices/MRP across Nykaa/Amazon.in/Flipkart — global dupe sites won't build it, Indian incumbents are conflicted against it.
- **Routine-level optimization** requires both skin models and formulation similarity — a genuine integration moat over single-axis players.

## 5. Customer Segments

- **Early adopter (beachhead): "The budget skintellectual"** — women & men 18–30 in metro/tier-1 India, active on r/IndianSkincareAddicts and Reels/Shorts dupe culture, spend ₹1,500–5,000/mo on skincare, research before buying, price-sensitive but efficacy-driven. They already juggle SkinSort + INCIDecoder manually (and complain both miss Indian brands) — we automate their workflow on the catalog they actually buy from.
- **Second segment:** skincare beginners overwhelmed by choice who want one answer, cheap ("just tell me what to buy") — a much larger pool in India than the beachhead.
- **Market size:** India BPC ~$28–30B with online beauty the fastest-growing channel; global skin-analysis app market ~$1.8B (2025) → $10B+ (2036); scan behavior validated in India by Cureskin's scale, dupe-culture demand by Reels dupe content and Indian SkinSort/INCIDecoder usage.

## 6. Channels

1. **Instagram Reels + YouTube Shorts organic** (TikTok is banned in India) — "I cut my skincare routine from ₹12,000 to ₹3,500" scan-and-save videos; the savings receipt is natively viral and WhatsApp-forwardable (primary bet).
2. **SEO** — "[expensive product] dupe for [skin type] India" long-tail pages; proven by SkinSort/Skinskool traffic globally, and Indian-brand dupe queries are nearly uncontested.
3. **Reddit/community** — r/IndianSkincareAddicts credibility plays (transparency reports, methodology posts); it's large, active, and exactly our beachhead.
4. **Explicitly avoid** paid Instagram funnels at Lóvi-style price points — that's the playbook that created their trust crisis.

## 7. Revenue Streams

- **Freemium subscription:** free = 1 scan + 1 routine + limited swaps; premium ~₹499/yr (below the impulse threshold for the beachhead, in Yuka's goodwill zone, and ~10× under Lóvi's ~$55 ≈ ₹4,600) for unlimited scans, re-scans/progress, full optimizer. Annual one-time payment via UPI at MVP — auto-renewal needs RBI e-mandate/UPI Autopay flows, defer that complexity. Price is GST-inclusive (18%).
- **Affiliate commissions** on purchase links — Amazon Associates India and Flipkart directly; Nykaa/Purplle via affiliate networks (Cuelinks/EarnKaro-class) — with a published neutrality policy: *rankings are set by fit + price, never commission* (disclose commissions per retailer to keep the Yuka-style trust halo).
- **Later (not MVP):** anonymized trend insights for brands (what dupes are winning per demographic) — only if it never touches ranking.
- **LTV hypothesis:** ₹499/yr sub + ~₹200/yr affiliate on ~₹8–10k routed spend at ~4–5% (net of network cuts) ≈ **₹700/user/yr**; must exceed blended CAC ≈ organic-led target <₹100.

## 8. Cost Structure

- **Fixed:** 2–3 person team (or solo + AI tooling); skin-analysis API license (Haut.AI-class, usage-priced in USD — a real forex exposure against ₹ revenue); infra ~₹40,000–1.5L/mo at MVP scale.
- **Variable:** per-scan API cost (the key unit economic — must stay under ~₹5/scan blended for a free tier to be viable at Indian ARPU), product-DB maintenance (scraping/licensing ingredient + ₹ price data across Nykaa/Amazon.in/Flipkart/Purplle), payment-gateway fees (~2%) + GST.
- **Biggest hidden cost:** keeping the product/price database fresh — Indian retailers run near-constant sale events, so this is an ops treadmill, not a one-time build.
- **CAC:** organic-first model targets near-₹0 paid; if Reels/Shorts organic fails, unit economics need re-validation before paid spend.

## 9. Key Metrics

- **North Star: verified ₹ saved per active user per month** (accepted swaps × price delta) — ties value delivery, retention, and virality into one number.
- **Activation:** % of new users who complete scan → routine → view ≥1 savings comparison in first session (target >50%).
- **Retention:** M1 return rate for re-scan or repurchase check (skincare replenishes on ~6–12 week cycles — retention loop = "time to re-buy").
- **Revenue:** free→paid conversion (target 3–5%), affiliate revenue per routed user.
- **Trust guardrail:** swap-acceptance rate and refund/complaint rate (if users reject swaps, the fit engine is failing; if complaints rise, we're becoming Lóvi).

---

## Riskiest assumptions (canvas → discovery hand-off)

1. Users trust an algorithm enough to *switch* products it recommends (not just browse dupes). ← riskiest, test first
2. Ingredient-similarity ≈ efficacy-similarity is credible without concentration data (Skinskool's admitted gap).
3. The savings artifact actually goes viral / drives organic CAC ≈ 0.
4. Affiliate + sub hybrid doesn't poison perceived neutrality.
5. Scan API costs allow a free tier.

**Fast validation ideas:** (1) landing page + waitlist with the "₹12,000 → ₹3,500" hook, measure signup rate; (2) concierge MVP — manually build 20 optimized routines for r/IndianSkincareAddicts/Instagram volunteers, measure swap acceptance and repurchase; (3) fake-door "see your routine's cheap twin" on a simple quiz app. Full assumption map in `docs/03-risky-assumptions.md`.
