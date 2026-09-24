# SkinMatch — Validation Experiments (Lean Startup / Pretotyping)

**Date:** 23 July 2026
**Principles:** measure behavior, not opinions (YODA — your own data); demand skin-in-the-game (time, money, or a real product photo — not just a "sounds cool").

---

## Cluster 1 — Data Foundation Audit *(tests F1; informs B3, S2)*

**Question:** Can we actually get full INCI lists for the Indian market?

**Method (desk audit, no code needed):**
1. Pull the top 100 best-selling skincare products across Nykaa + Amazon.in (25 each: cleansers, moisturizers, serums, sunscreens — mix of Indian D2C and imported).
2. For each, attempt to obtain the **full** INCI list from: listing page → brand website → packaging photos in reviews. Cap effort at 10 min/product. Log source and time taken.

**Metrics & thresholds:**
- 🟢 **≥70%** full-INCI coverage → foundation viable; proceed
- 🟡 50–69% → viable with manual/crowdsourced backfill; model that cost before building
- 🔴 **<50%** → foundation fails as scoped; investigate alternate sources (CDSCO filings, importer labels) or kill

**Effort:** 2–3 days · **Cost:** ₹0

---

## Cluster 2 — Demand & Conversion Funnel *(tests V1, G2; free reads on G1, G4, V6)*

**XYZ hypothesis:** *At least 15% of Indian skincare-interested visitors who reach the SkinMatch landing page will join the waitlist, and at least 30% of joiners will submit a real product they want analyzed.*

**Experiment 2a — Landing page + waitlist (skin-in-the-game ladder)**
- One-page site: the two sharpest promises (find cheaper dupes with ingredient match; check if a product is safe *for your skin*). Email waitlist signup.
- Commitment ladder after signup: 3-question survey (platform preference → tests G4; current tools; biggest frustration) → then "upload a photo of a product label you want us to analyze." A photo upload is a **time-investment signal** far stronger than an email.
- Thresholds: 🟢 ≥15% visitor→waitlist AND ≥30% waitlist→product-submission · 🔴 <5% visitor→waitlist with ≥500 visitors → strong kill signal for tool demand.

**Experiment 2b — Content-to-tool conversion test**
- Publish 5 pieces over 2 weeks in r/IndianSkincareAddicts + Instagram: 3 dupe breakdowns ("₹2,400 serum vs ₹549 serum — ingredient lists side by side"), 2 claim-checks ("'niacinamide serum' — it's the 12th ingredient"). Each links to the landing page.
- Metrics: content engagement (tests V6), content→page CTR (tests G1/G2). Threshold: 🟢 ≥2% viewer→click · 🔴 high engagement but ~0% click-through = people want *content*, not a *tool* — the G2 failure mode, a pivot signal toward media-first.

**Effort:** 1–2 days page + ~4 days content · **Cost:** ₹0–10,000 (optional paid boost)

---

## Cluster 3 — Dupe Value Chain *(tests F2 → V2, V3 — sequenced)*

**Gate order matters:** no point testing whether users switch on dupes experts would reject.

**Experiment 3a — Expert endorsement panel (F2)**
- Using Cluster 1 data, hand-generate 20 dupe pairs with a spreadsheet INCI-similarity score (shared actives weighted > shared excipients; penalize missing key actives).
- 2 cosmetic chemists or dermatologists rate each pair: "endorse as functionally similar / partially / reject" (paid consults, ~₹2–5k each).
- Thresholds: 🟢 ≥60% endorsed → similarity approach credible · 🔴 <40% → concentration-blindness is fatal to match-%; pivot framing to "contains the same key actives" rather than a similarity score.

**Experiment 3b — Concierge dupe service (V2, V3)**
- Invite 30 waitlist/community members: "Send us a product you love but find expensive — we'll send 2 cheaper ingredient-matched alternatives with buy links." Deliver manually over WhatsApp/email using audit data + 3a-validated pairs.
- **V3 framing A/B:** half get "87% ingredient match", half get "contains the same key actives (5% niacinamide, zinc PCA)". Compare click-through per variant.
- Metrics: request rate (interest), **affiliate-link CTR (behavior)**, 2-week follow-up purchase/intent.
- **XYZ:** *At least 40% of recipients will click a buy link, and at least 15% will report purchasing (or carting) the dupe within 2 weeks.*

**Effort:** 3a: 3–4 days · 3b: ~1 week rolling · **Cost:** ~₹5–10k expert fees

---

## Cluster 4 — Economics Model *(tests B1, B2)*

**Experiment 4a — Unit-economics desk model**
- Build a spreadsheet with **researched** (not assumed) inputs: real affiliate rates (Amazon Associates India beauty; Nykaa/Flipkart via EarnKaro/Cuelinks), category AOVs (₹400–1,500), click→purchase rates (1–5%), purchases/user/year.
- Stress scenario for B2: dupes cut AOV 40% — what's blended revenue/MAU? What premium price at 1–2% conversion closes the gap?
- Threshold: 🟢 at least one credible scenario ≥ break-even per MAU (or a plausible premium path) · 🔴 no scenario works → monetization pivot required *before* any build decision.

**Experiment 4b — Live affiliate check (piggyback)**
- Register affiliate accounts; put real links in Cluster 2 content and Cluster 3b messages. Measure actual clicks, attributed purchases, and real (not published) commission rates.

**Effort:** 4a: 2–3 days · 4b: 0.5 day setup · **Cost:** ₹0

---

## Cluster 5 — Sensitive-Skin Reality *(tests V4, U1, E1; V7 add-on)*

**Experiment 5a — Mom-Test interviews (V4)**
- 10 self-described sensitive-skin users (recruit via waitlist + communities). Past behavior only: "Tell me about your last reaction. What caused it? How do you check products now?"
- Metric: % who can name ≥1 specific trigger ingredient (vs. vague "chemicals").
- Interpretation: 🟢 ≥60% name triggers → self-declared avoid-lists work · 🟡 <40% → **pivot the feature**: guided trigger-discovery (elimination flow) instead of self-declared filters — the draft's assumption inverts from "filter by known triggers" to "help me find my triggers."

**Experiment 5b — Quiz + traffic-light pretotype (U1, E1)**
- 60-second Typeform quiz → manually produced traffic-light one-pager for 2 products the user already owns.
- Watch for: verdicts contradicting lived experience (U1 failure) and **green = "guaranteed safe" over-trust** (E1 danger). Test whether patch-test guidance registers.

**Experiment 5c — Concierge AI routine (V7)**
- For 10 beginners: Claude-generated routine within their stated budget, manually reviewed against derm-sourced rules, delivered as a PDF via WhatsApp.
- **XYZ:** *At least 50% will start the routine within 2 weeks, and at least 30% will come back asking for an adjustment* (a return-adjustment request is the engagement signal the AI-routine bet lives on).

**Effort:** interviews ~1 week elapsed · 5b/5c: 2–3 days each · **Cost:** ~₹2–5k incentives

---

## Three-week schedule

| Week | Running |
|------|---------|
| **1** | Cluster 1 audit · Cluster 4a econ model · build landing page (2a) · first 2 content pieces (2b) · recruit experts + interviewees · affiliate signups (4b) |
| **2** | Content cadence continues; waitlist accumulating · 3a expert panel (uses audit data) · 5a interviews · live affiliate links |
| **3** | 3b concierge dupes · 5b quiz pretotype · 5c concierge routines (follow-ups spill into week 4) · synthesis + decision memo |

**Decision gate: end of week 3** (purchase-intent follow-ups land week 4).

## Decision framework

> **Superseded 23 July 2026:** the founder committed to a full production build, so the build/kill gates below no longer gate the build. See the reframed decision framework in `../Discovery Plan.md` — experiments now settle design choices (data strategy, dupe framing, sensitivity model, platform, monetization architecture), and the thresholds below serve as warning lights only.

| Signal pattern | Call |
|----------------|------|
| F1 ≥70% · waitlist ≥15% · product-submission ≥30% · expert endorsement ≥60% · dupe CTR ≥40% | **Build** — MVP = ingredient DB + dupe finder + basic profile filters (draft Steps 1–2 compressed) |
| Demand strong but dupe chain weak (3a/3b fail) | **Pivot** — lead with safety/traffic-light wedge (Bet B), dupes become "same key actives" content |
| Content engagement strong but conversion ~0 (G2 fails) | **Pivot** — media-first: build the audience, sell the tool later |
| V4 fails (<40% know triggers) | **Pivot feature** — guided trigger-discovery replaces self-declared avoid-lists |
| F1 <50% with no alternate source, or landing <5% at ≥500 visitors, or no viable econ scenario | **Kill** — the honest outcome this discovery was designed to allow |

**Total discovery budget: ~₹15–30k + ~3 weeks of part-time effort. No code beyond a landing page.**
