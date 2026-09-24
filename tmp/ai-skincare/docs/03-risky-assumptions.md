# Risky Assumptions & Validation Plan — AI Skincare Advisor + Dupe Finder

**Product:** face-scan analysis + personalized routines + routine-level cheapest-alternative optimization.
**Framework:** 8 risk categories (Torres' 4 core risks + Ethics, GTM, Strategy, Team).
**Rule of thumb:** assume ~¾ of these hopes are wrong until tested.
**Confidence:** 🟢 high (evidence exists) · 🟡 medium (plausible, untested) · 🔴 low (pure hope — test first)

---

## Priority matrix — what to test first

**Kill-shot assumptions (🔴 high-impact, low-evidence — the product dies if false):**

| # | Assumption | Cheapest test |
|---|---|---|
| V2 | Users will actually *switch* to recommended cheaper products, not just window-shop dupes | Concierge MVP: hand-build 20 optimized routines for volunteers, measure swap acceptance + 6-week repurchase |
| V1 | "Personalized + cheaper" beats free generic dupe sites enough to pay for | Landing page with "₹12,000 → ₹3,500" hook; measure waitlist conversion vs. a generic-dupe control page |
| E1 | Ingredient-similarity ≈ efficacy claim survives scrutiny without concentration data | Post methodology on r/IndianSkincareAddicts; count chemist takedowns vs. endorsements |
| G1 | The savings receipt goes viral → CAC ≈ 0 | Post 10 scan-and-save Reels/Shorts pre-product; measure view/follow/waitlist rates |

If V2 or V1 fails, stop. If E1 fails, reposition claims ("similar formula" not "same results"). If G1 fails, revisit unit economics before building.

---

## 1. Value risk

- **V1 🔴** Budget skintellectuals will pay ~₹499/yr for personalization *on top of* free tools (SkinSort, INCIDecoder) they already use — Indian subscription willingness-to-pay is notoriously low outside entertainment. *Test:* fake-door pricing page on the waitlist; measure "notify me at launch price" opt-in.
- **V2 🔴** Users trust the algorithm enough to switch products — skincare is anxiety-laden ("what if I break out?"); saving ₹800 may not overcome fear of a ₹500 mistake on their face. *Test:* concierge MVP swap-acceptance rate; target >30% of proposed swaps accepted.
- **V3 🟡** Value persists after the first big optimization — once your routine is cheap, why return? *Test:* in concierge cohort, measure any return trigger (re-scan, new product check, repurchase reminder) at 6–8 weeks.
- **V4 🟢** Demand for AI skin analysis exists (Lóvi's growth despite hostile reviews; SkinGenie's traction; 80M Yuka users prove scan behavior).

## 2. Usability risk

- **U1 🟡** Users can produce a usable face scan (lighting, makeup, camera quality) without frustration-churn. *Test:* wizard-of-oz scan flow with 10 users; completion rate + retake count.
- **U2 🟡** "Fidelity %" and fit-vs-price trade-offs are comprehensible to beginners without a chemistry lecture. *Test:* show 5 mock swap cards to 10 target users; ask them to explain back why the swap is safe. >7/10 correct = pass.
- **U3 🟡** Onboarding (scan → profile → routine → savings) fits in one session under 5 minutes before attention dies. *Test:* prototype funnel drop-off measurement.

## 3. Viability risk

- **B1 🔴** Hybrid monetization (subscription + affiliate) doesn't poison neutrality perception — the exact tension Yuka avoided by refusing affiliate money entirely, and the exact conflict Cureskin embodies (own-brand kits). *Test:* A/B messaging with/without "we earn commissions, rankings unaffected" disclosure; measure trust-survey delta and waitlist conversion.
- **B2 🟡** Affiliate programs (Amazon Associates India, Flipkart Affiliate, Nykaa/Purplle via networks like Cuelinks/EarnKaro) will accept and not ban an app that systematically diverts sales from premium to budget brands — and their commission rates on beauty actually support the LTV math. *Test:* desk research + apply to 3 programs pre-launch; read ToS for "comparison site" clauses; confirm real beauty-category rates.
- **B3 🟡** Unit economics: scan API + data-ops costs < revenue per user (LTV ~₹700/yr hypothesis) — tighter than Western markets because the API is priced in USD and revenue is in ₹; blended scan cost must stay under ~₹5. *Test:* price out Haut.AI/Perfect Corp API tiers; spreadsheet model at 1k/10k/100k users.
- **B4 🟡** A solo/small team can sustain the product+price database ops treadmill — Indian retailers run near-constant sales, and nobody maintains a fresh Indian-catalog INCI+price dataset today (that's both the burden and the moat). *Test:* build scraper POC for 2 retailers (Nykaa + Amazon.in); measure weekly maintenance hours honestly.

## 4. Feasibility risk

- **F1 🟢** Skin analysis is buildable via API (Haut.AI Face Analysis 3.0, Perfect Corp are commercially available) — buy, don't build.
- **F2 🔴** A fit+price ranking engine that produces *defensibly good* matches from ingredient lists alone — without concentrations, formulation order tells only part of the story (Skinskool publicly admits this ceiling). *Test:* build scoring POC on 50 known dupe pairs (community-validated dupes as ground truth); measure agreement with expert/community consensus.
- **F3 🟡** Product + ingredient + multi-retailer ₹ price data is obtainable at sufficient coverage (license, scrape, or partner) without legal exposure — for the *India-relevant* top 500 (Indian D2C + K-beauty-in-India + Nykaa-available prestige), which no existing dataset covers well. *Test:* audit SkinSort/INCIDecoder ToS, check for open datasets/APIs, estimate coverage of the India-relevant top-500.
- **F4 🟡** Price freshness across Nykaa/Amazon.in/Flipkart/Purplle is maintainable (prices/promos change daily; sale events like Nykaa Pink Friday and Flipkart Big Billion Days swing prices violently; MRP vs. selling price must be tracked separately). *Test:* same scraper POC as B4; measure staleness rate after 2 weeks.

## 5. Ethics risk

- **E1 🔴** Claiming a ₹599 product "works like" a ₹4,500 one for *your skin* is an efficacy claim we can't fully prove — overclaiming risks user harm (reactions, wasted money), chemist-community backlash, and exposure under India's advertising/claims rules (ASCI code; Drugs & Magic Remedies Act if wording drifts toward treatment claims). *Mitigation:* language discipline ("formulation match," not "same results"), confidence intervals, patch-test prompts, allergen flags from the user's stated sensitivities.
- **E2 🟡** Face images are personal data under India's **DPDP Act 2023** (plus SPDI Rules) — and DPDP treats everyone under 18 as a child requiring verifiable parental consent, while skincare content skews young. Storing scans of possibly-minor Instagram users is a real liability. *Test:* legal review before launch; default to on-device or immediate-delete processing; 18+ age gate; vendor DPA + check where the scan API processes data (cross-border transfer posture).
- **E3 🔴** Skin-analysis models underperform on darker skin tones (documented industry bias) — in India this isn't an edge case, it's the *entire user base* (predominantly Fitzpatrick IV–VI). A vendor tuned on Western datasets could mis-score pigmentation/acne for most Indian users. Upgraded from ethics checkbox to hard vendor-selection gate. *Test:* vendor-API accuracy audit across Indian skin tones before choosing supplier.
- **E4 🟢** Business model is user-aligned (we make money when users save money) — the anti-Lóvi. Guard it: no dark-pattern trials, one-tap cancel.

## 6. Go-to-Market risk

- **G1 🔴** Scan-and-save content achieves organic virality on Instagram Reels/YouTube Shorts (the whole CAC model rests on this — TikTok is banned in India, so its dupe-culture playbook must transfer to Reels). *Test:* 10 pre-product Reels/Shorts using manual comparisons; ≥1 video >50k views or waitlist CPA <₹30 = signal.
- **G2 🟡** SEO dupe pages can carve share from SkinSort/Skinskool's entrenched global rankings — likely easier in India: "[Indian product] dupe" and "dupe in India" long-tail queries are nearly uncontested. *Test:* publish 10 programmatic "[product] dupe for [skin type] India" pages; measure impressions in 60 days.
- **G3 🟡** r/IndianSkincareAddicts tolerates a commercial product (subreddits are hostile to self-promotion; one mod ban ends the channel). *Test:* engage as methodology-transparent builder first ("I built a tool, roast my algorithm"); measure reception.
- **G4 🟡** Timing: dupe culture is still ascending in India in 2026–27, not cresting. *Monitor:* Google Trends India "skincare dupe," Reels/Shorts hashtag velocity quarterly.

## 7. Strategy & Objectives risk

- **S1 🔴** The 12–18 month window closes if an incumbent moves first: SkinSort (has the database, needs a scanner + Indian coverage), Nykaa/Tira (has distribution + purchase data, could white-label a Perfect Corp analyzer in-app), or Cureskin (has Indian scan scale, could open to third-party products). *Mitigation:* speed + own the data flywheel (swap-acceptance data) they can't backfill + the neutrality position retailers/own-brand apps structurally can't take; monitor their releases monthly.
- **S2 🟡** Brands/retailers won't retaliate (delisting from affiliate programs, legal threats over comparison claims). India context: comparative advertising is legal if factual and non-disparaging, but Indian FMCG incumbents do litigate (HUL-style disparagement suits) and ASCI complaints are the realistic vector — factual INCI comparison with language discipline stays clear. *Test:* covered by B2 desk research + counsel read on comparative-claims exposure.
- **S3 🟡** "Save money" positioning doesn't trap us in a low-WTP segment that never upgrades — a sharper risk in India where free alternatives are the norm. *Test:* track free→paid conversion in beta against the 3–5% target.
- **S4 🟢** No single-point platform dependency at MVP (web-first avoids Play Store/App Store approval and fee risk; India's ~95%-Android market makes a PWA with web push genuinely viable; native later).

## 8. Team risk

- **T1 🟡** Solo founder/small team covers ML-adjacent engineering + data ops + consumer growth content simultaneously — three different jobs; the growth-content job (near-daily Reels/Shorts) is the one founders most often drop. *Test:* honest 4-week time audit during concierge MVP; if content cadence dies first, hire/partner there.
- **T2 🟡** No dermatology/cosmetic-chemistry credibility on the team — Cureskin has a derm network, Lóvi a medical board; our claims need *someone* credentialed to survive scrutiny (India has a deep bench of derm/chemist creators to recruit from). *Test:* recruit 1 cosmetic chemist or dermatologist advisor (equity/hourly) before public methodology post.
- **T3 🟢** Modern AI tooling makes the MVP buildable solo (scan API + scoring engine + web app is weeks, not years).

---

## Recommended sequence (next 4–6 weeks)

1. **Week 1–2:** Landing page + "₹12,000 → ₹3,500" Reels/Shorts (tests V1, G1) — no code beyond a page.
2. **Week 2–4:** Concierge MVP with 20 volunteers from waitlist/r/IndianSkincareAddicts (tests V2, U2, E1).
3. **Week 3–4 (parallel):** Scoring POC on 50 known dupe pairs (India-relevant products) + scan-API pricing/Indian-skin-tone bias audit (tests F2, B3, E3).
4. **Gate:** proceed to build only if V1 (waitlist converts), V2 (swaps accepted), and F2 (scoring credible) all pass.
