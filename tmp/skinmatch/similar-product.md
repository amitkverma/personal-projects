# Similar Product: Lóvi (iOS)

**Source:** https://mobbin.com/apps/lovi-ios-a3579a78-5f71-4605-8b4f-07b28595c3f5/edb007ea-76af-4349-a20e-6c02973808ec/flows
**Reviewed:** 2026-08-30 (from Mobbin flow captures dated Dec 2025)
**Web version:** https://claude.ai/code/artifact/47708f3f-632c-49ee-8a42-be131dfe972c

---

## What it is

An AI skincare companion. It combines a **face scanner** (diagnoses skin concerns from a selfie), a **cosmetics scanner** (rates any product's "fit" for your skin), a **personalized daily routine** with affiliate product picks, and an **AI cosmetologist chat** — wrapped in a habit-loop "Daily Plan" and monetized via subscription.

Brand voice: a friendly smiley mascot ("Lóvi") with medical credibility layered on top ("Lóvi MD Verified", a named Medical Director who "approves" products).

---

## High-level features

| # | Feature | What it does |
|---|---|---|
| 1 | **Skin Profile quiz** | Conversational questionnaire: main goal, sensitivity, skin type, concerns (dark circles, oiliness, sagging, crow's feet, puffy eyes, texture…), chronic conditions (rosacea, eczema, psoriasis, atopic dermatitis), age, gender, budget tier ($19-and-less → $100+), current routine products, K-beauty preference. Editable later under *My Skin Profile* / *Routine Preferences*. |
| 2 | **AI Face Scanner** | Camera capture → annotated analysis by concern (wrinkles, freckles, post-acne spots, etc.) and face zone (cheeks / forehead / chin). Includes a **"Main Goal Validation"** that checks whether the user's stated goal aligns with what the scan actually found. Limited free scans; more behind Premium. |
| 3 | **Progress Tracking** | Timeline of past face scans with status ("You are on track!") — the retention hook for re-scanning. |
| 4 | **Cosmetics & Food Scanner** | Scan a product (or upload a photo / search by name) → **"80% fit for you"** score broken into Skin-type fit, Effectiveness, Safety. Also covers food, beverages, supplements. Limited free scans ("2 scans left"). |
| 5 | **Product detail page** | Fit score, "Lóvi Assistant Explains", How to Apply (with video tutorial), aggregated **"People Say"** review synthesis (rating, pros/cons, sources cited: ulta, makeupalley, youtube…), Formulation / key ingredients, cited regulatory sources (FDA, ECHA, TGA, EWG, PubMed, CIR), and a named Medical Director approval with signature. Buy on Amazon (affiliate). Add to Shelf / Wishlist. "Wrong?" report button. |
| 6 | **Routine for You** | Generated "Routine Formula" from profile + scan (shows all inputs + last-updated timestamp + "Update Formula"). Morning / Evening / Weekly tabs, step-by-step (Pre-cleanser → Cleanser → … → SPF), each step with "Why we picked it", fit %, price, and 5 alternatives. **Buy Routine** bundles it at Essential / Advanced / All Extra tiers with a running cart total. |
| 7 | **Products hub** | Search (rate-limited on free), curated shelves by concern ("Barrier-Boosting Spot Treatments", "Hydrating Spot-Fading Serums", "Soothing Spot Patches"), My Shelf, Wishlist, Recent Scans. |
| 8 | **Today / Daily Plan** | 7-day checklist home screen: *First Steps* (tutorial tasks), *Daily Plan* (Morning routine, Evening routine, MD greeting), *Skin Diary* mood check-in (Bad → Awesome), routine cards, Ask Lóvi prompt chips, Daily Affirmation (tap to reveal, shareable). |
| 9 | **Ask Lóvi — AI Cosmetologist** | Chat with suggested prompts, personalized to the user's actual products ("continue using the Neogen Niacinamide Serum in your PM routine…"), chat history, bookmarking, follow-up suggestion chips. |
| 10 | **Insights** | Editorial content: "Lóvi 101" explainers, "Skincare Trends through a science lens", massage tutorials, and paid **Handcrafted Skincare Guides** by the medical team (e.g. Hair Treatment Guide — $9.99 lifetime one-off). |
| 11 | **Monetization** | *Lóvi Premium* paywall (weekly $7.99 / yearly $49.99, 3-day free-trial toggle, promo code, restore), one-off guide purchases, Amazon affiliate on every product, and a **referral gift card** (5 × 7-day passes to give friends). |
| 12 | **Sunshine (Profile)** | Skin Profile, Routine Preferences, Routine, Shelf, Progress Tracking, Subscription mgmt, FAQ, App Settings, Suggest a Feature, Contact, social links. |

**Tab bar:** Today · Products · New Scan (center) · Insights · Sunshine (profile)

---

## User journey

### First session (onboarding → paywall → routine)

```
Splash → "Hi, I'm Lóvi! Here to help you boost your skincare results"
   ↓
Skin quiz
  goal → sensitivity → skin type → concerns → chronic conditions
  → budget → current products → K-beauty preference
   ↓
Behavioral-science nudge
  "Let's commit to care about yourself" → "Yaaaaay!" (cites NLM meta-analysis on nudging)
   ↓
Email capture ("save progress")
   ↓
AI Face Scan prompt → camera permission → privacy / photo-training consent → capture
   ↓
Skin Analysis results (by concern & zone) → Main Goal Validation
   ↓
Loading screen: "Tailoring your skincare program… 47,750 products in the Lóvi database"
   ↓
PAYWALL — Unlock Lóvi Premium
  before/after imagery · Build a routine / Boost results / Track progress
  free-trial toggle · weekly vs yearly · promo code · restore
   ↓
"Your new routine is ready!" → Morning / Evening / Weekly steps → Buy Routine bundle
   ↓
HOME (Today tab) — Day 1 of 7 checklist
```

### Ongoing loop

1. **Open Today** → tick off Morning / Evening routine → log Skin Diary mood → read affirmation.
2. **Shopping moment** → New Scan → Cosmetics → fit score → buy / add to shelf / ask Lóvi about it.
3. **Question** → Ask Lóvi chat, grounded in the user's own routine.
4. **Periodically** → New Scan → Face → compare in Progress Tracking → routine formula updates.
5. **Curiosity** → Insights articles & guides (some paid).

---

## Design patterns worth noting

- **Scan-gated funnel.** Value is demonstrated (face analysis) *before* the paywall; the paywall sits between "diagnosis" and "prescription" (the routine).
- **Trust stacking on every product.** Fit %, MD-verified badge, named expert with signature, regulatory source logos, synthesized reviews with sources. Heavy emphasis on "non-affiliated / non-sponsored" picks even though purchases route through Amazon.
- **Scarcity as monetization.** "2 scans left", "No free scans" on Face, "Search cosmetics (2 left)".
- **Skin Profile as single source of truth.** Every recommendation says "based on your skin profile"; every profile edit promises to "refresh your recommendations". The Routine Formula card exposes all inputs transparently.
- **Habit scaffolding.** 7-day day tabs, checklist gamification, mood diary, affirmations, behavioral-science citations in onboarding.
- **Persona mascot** carries the whole app (speech bubbles, floating button, chat avatar) — softens the clinical content.
- **Explainability everywhere.** "Why we picked it" per routine step, "Lóvi Assistant Explains" per product, "Main Goal Validation" per scan.

---

## Mobbin flows referenced

Onboarding · Answering questionnaires · Completing account setup · Scanning face · New scan · Scanning a product · Searching a product · Scans · Products · Routine for you · Buy routine · Updating routine preferences · Skin profile · Progress tracking · Subscribing to Lóvi Premium · Gift card · Home · Article detail · Guide detail

> Note: the Mobbin web page returns 403 to unauthenticated fetches; this breakdown was assembled from Mobbin's MCP flow/screen data.
