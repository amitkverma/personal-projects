# SkinMatch — Assumption Map (New Product, 8 Risk Categories)

**Date:** 23 July 2026
**Scope:** 4 bets + 1 foundation carried forward from `01-ideas-brainstorm.md`
**Bets:** A = Dupe Finder + price tracking · B = Traffic-light safety + scan camera + Skin ID quiz · C = Claim Checker · D = AI routine builder + concern mapping · F = Indian ingredient database

Confidence scale: **High** = safe to assume for now · **Medium** = worth checking · **Low** = dangerous to assume, must test.

---

## Devil's advocate — three perspectives on why SkinMatch fails

**PM says:** "The ingredient-literate buyer in India is a loud but tiny niche, already served free by Instagram dupe reels, YouTube dermatologists, and INCIDecoder. The mass market buys on brand trust and influencer recommendation. And your revenue model pays you a commission for sending people to *cheaper* products — you've built a machine that shrinks its own basket size."

**Designer says:** "People don't actually know their skin. They'll answer the quiz wrong, get a confident-looking traffic light built on bad inputs, react to a 'green' product, and never trust you again. And the in-store scan magic moment dies the first time OCR chokes on a curved bottle with 6-point fonts under store lighting."

**Engineer says:** "Ingredient lists don't tell you concentrations. Two products with 90% INCI overlap can perform completely differently. Your dupe engine can be *technically correct and cosmetically wrong* — and the DB it runs on doesn't exist yet: Indian e-commerce listings routinely omit or truncate INCI lists, Nykaa has no public API, and scraping three hostile marketplaces is a treadmill, not a milestone."

---

## Master assumption list

### Value — will they want it?

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| V1 | A meaningful segment of Indian skincare buyers wants to decide by ingredients, not brand/influencer trust — and wants a *tool* for it, not just content | All | **Medium** | Landing-page smoke test + skincare community survey |
| V2 | Buyers coveting an expensive product will actually switch to an ingredient-similar cheaper one (they're buying results, not status) | A | **Low** | Fake-door dupe results with "buy cheaper" CTA; measure clicks |
| V3 | "87% ingredient match" is credible to users as a proxy for "works the same" | A | **Low** | Concierge dupe service; interview reactions to match framing |
| V4 | Sensitive-skin users know their trigger ingredients well enough to set up a useful avoid-list | B | **Low** | 10 interviews with self-described sensitive-skin users |
| V5 | Scanning a label in-store is a behavior people will actually adopt at the shelf | B | **Medium** | Wizard-of-Oz in-store test; behavioral survey |
| V6 | "The label is lying to you" claim-checks resonate enough to drive shares and installs | C | **Medium** | Post 5 claim-check breakdowns as content; measure engagement |
| V7 | Beginners will trust an AI-built routine over influencer/derm recommendations | D | **Low** | Concierge routine service; willingness-to-follow interviews |
| V8 | Users return between purchases (~1–3 month cycles) instead of using once and deleting | All | **Low** | Deferred — retention only testable post-MVP; design re-engagement hooks now |

### Usability — can they figure it out?

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| U1 | A 60-second quiz captures a skin profile accurately enough that verdicts feel right (self-misclassification of skin type is common) | B | **Medium** | Quiz prototype vs. dermatologist assessment on 15 users |
| U2 | OCR reliably reads real Indian product labels — tiny fonts, curved bottles, glare, bilingual packaging | B | **Low-Medium** | Technical spike: ML Kit/Vision API on 50 photographed labels |
| U3 | Ingredient science can be presented without overwhelming beginners | All | **Medium** | Prototype test with 5 beginners; comprehension check |
| U4 | Users can meaningfully steer the AI routine via natural language ("make it cheaper") | D | **High** | Defer — standard LLM capability, test post-build |

### Viability — does the business work?

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| B1 | Affiliate commissions (India beauty: roughly 4–10% via Amazon Associates, EarnKaro/Cuelinks for Nykaa) on realistic funnels produce meaningful revenue per user | All | **Low** | Unit-economics model with real rates + one live content page with affiliate links |
| B2 | The dupe model isn't self-defeating — commissions on cheaper products still net out (or premium/other revenue compensates) | A | **Low** | Same model as B1; scenario analysis |
| B3 | A small team can sustain DB maintenance + price scraping ops cost | A, F | **Medium** | Cost model after the F1 data audit |
| B4 | Price aggregation via scraping/affiliate APIs is legally tolerable (ToS, anti-bot) | A, F | **Medium** | Legal review of marketplace ToS + affiliate API capabilities |
| B5 | Claim Checker won't trigger defamation/disparagement action from Indian brands — or we can frame it defensibly (facts from the label only) | C | **Low-Medium** | Legal opinion; publish 5 pieces framed as factual INCI reporting, monitor |

### Feasibility — can we build it?

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| F1 | Full INCI lists are obtainable for the majority of top-selling Indian skincare products (e-comm pages, brand sites, packaging photos) | F (all) | **Medium** | **Data audit spike**: sample 100 top sellers, measure INCI coverage % |
| F2 | INCI-list similarity scoring produces dupes a cosmetic chemist/derm would endorse, despite unknown concentrations | A | **Low** | Generate 20 dupe pairs; expert panel rates endorsement rate |
| F3 | Price freshness across 3 marketplaces is maintainable against anti-bot measures | A | **Medium** | Scraper spike: 2-week reliability run on 50 products |
| F4 | LLM + derm-reviewed rules engine can reliably prevent harmful routine advice | D | **Medium** | Red-team eval set (pregnancy, cystic acne, prescription actives) |
| F5 | Crowdsourced INCI contributions will materialize to fill DB gaps (cold-start) | F | **Low** | Defer — depends on having an audience first |

### Ethics — should we build it?

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| E1 | A green "safe for you" light won't cause harm via false reassurance — patch-test guidance and confidence framing are sufficient mitigation | B | **Medium** | Derm advisor review of verdict UX; copy test |
| E2 | Disclaimers genuinely suffice for the medical-advice boundary (cystic acne, melasma need dermatologists; the app must know when to say "see a doctor") | D | **Medium** | Rules-engine escalation criteria reviewed by derm |
| E3 | Claim-check verdicts can be kept accurate and fair enough to responsibly publish | C | **Medium** | Editorial standard + expert review pre-publish |
| E4 | Skin-concern data (health-adjacent personal data under India's DPDP Act 2023) can be handled compliantly without killing UX | All | **High** | Standard compliance work; verify at build time |

### Go-to-Market — can we reach and convert them?

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| G1 | Ingredient-curious Indians are cheaply reachable via Instagram/YouTube skincare communities and SEO ("dupe for X", "is X safe") | All | **Medium** | Keyword volume research + 2-week organic content test |
| G2 | Content viewers convert into tool users (not just free-content consumers) | All | **Low** | Content posts with waitlist CTA; measure view→signup rate |
| G3 | The ingredient-literacy wave in India is still rising (right timing) | All | **High** | Market signal review (Minimalist growth, search trends) |
| G4 | Web-first launch works for this audience (lower friction than app install) | All | **Medium** | Waitlist survey: platform preference question |
| G5 | Skincare influencers will partner despite the app undercutting brands they promote | All | **Low-Medium** | Outreach to 10 micro-influencers; gauge response |

### Strategy & Objectives

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| S1 | Nykaa/Amazon won't quickly copy ingredient-first discovery; independence ("we don't sell products") is a durable differentiator | All | **Medium** | Monitor; not directly testable — mitigate via speed + moat |
| S2 | The Indian INCI database compounds into a real moat | F | **Medium** | Validated indirectly by F1 (how hard was it to build?) |
| S3 | India is the right beachhead vs. English-speaking global | All | **Medium** | Revisit after G1/G2 signal |
| S4 | Global players (INCIDecoder, Skinsort, Yuka) won't localize to India first | All | **Medium-High** | Monitor their release notes/coverage |

### Team

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| T1 | The team (currently solo?) covers data engineering + LLM + consumer app + content creation, or can close gaps | All | **Unknown** | Honest skills inventory against the MVP scope |
| T2 | Dermatologist advisors can be recruited affordably for credibility and safety review | B, D | **Medium** | Outreach to 5 derms; gauge interest/cost |
| T3 | Runway and motivation sustain a 6–12 month validate-then-build journey | All | **Unknown** | Founder decision, not a test |

---

## Cross-cutting observations

1. **The riskiest cluster is Value for Bet A** (V2, V3, F2 together): the dupe finder is the most differentiated idea, but it stands on three unproven legs — people switch, people believe match %, and matches are actually good.
2. **The foundation gates everything**: if F1 fails (INCI lists unobtainable at scale), every bet degrades. It's also the *cheapest big assumption to test* — a pure desk audit.
3. **The business model has a structural tension** (B2): success at saving users money reduces per-transaction revenue. Needs a model, not a feeling.
4. **B's safety promise carries the highest harm-if-wrong** (V4 + E1): personalization built on unreliable self-knowledge could hurt users and the brand.
