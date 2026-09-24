# SkinMatch PIVOT — Assumption Map (New & Changed Assumptions)

**Date:** 23 July 2026
**Scope:** Influencer-consensus pillar + foundations, from `05-pivot-brainstorm.md`. The ingredient pillar's assumptions in `02-assumptions.md` still stand; this map covers what the pivot **adds or changes**. IDs prefixed P to avoid collision.
**Bets:** A = Consensus Score + budget-swap routines · B = Receipts UI + Trend radar · F = mining pipeline + entity resolution + endorsement graph

---

## Devil's advocate — why the pivoted product fails

**PM says:** "Nobody wakes up wanting a *consensus*. Skincare trust is parasocial — people trust *their* creator, not fourteen strangers averaged together. And your acquisition channel is your data source: you're mining creators' content to build a product that intercepts their affiliate revenue, then hoping those same creators don't turn their audiences against you."

**Designer says:** "A consensus score looks exactly like every fake review count on the internet. Why would anyone believe '14 creators recommend' from an app they've never heard of — especially when tapping through to receipts shows 8-second clips stripped of context? And if a user came from a reel wanting *that exact serum*, offering them a cheaper swap isn't a feature, it's a bait-and-switch."

**Engineer says:** "'I stopped using this because it broke me out' contains a product mention with positive-sounding words around it. Extraction that can't distinguish endorsement from mention from criticism poisons the whole graph. Undisclosed sponsorship detection is a research problem, not a sprint task. And you just doubled your foundations: the INCI database was one moat to dig, now there's an endorsement graph on top — same small team."

---

## Master assumption list (new & changed)

### Value

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PV1 | Users value *aggregated* consensus over their one trusted creator's word (parasocial trust transfers to a number) | A | **Low** | Framing A/B in content + landing page; interviews |
| PV2 | Users care whether a recommendation is sponsored — sponsorship-discounting is a felt differentiator, not an insider concern | A | **Low-Medium** | A/B: "14 creators" vs "14 creators, 11 unsponsored" — measure engagement lift |
| PV3 | Influencer-inspired buyers accept **budget swaps** in a creator-derived routine (they want the *outcome*, not the exact SKU) | A | **Low** | Concierge routine with optional swaps; measure swap acceptance rate |
| PV4 | Consensus routines are actually *good* routines — creator content skews actives-heavy and trend-driven; averaging it may produce derm-disapproved stacks | A | **Low-Medium** | Derm panel reviews 10 consensus-generated routines |
| PV5 | Aggregation beats "just watching YouTube" — the tool saves enough time/confusion to earn a visit | A, B | **Low-Medium** | Demand funnel: does the promise convert to waitlist + product submissions? |
| PV6 | Receipts and Trend radar drive *return* visits between purchases | B | **Medium** | Defer core test to post-launch; proxy via content engagement |

### Usability

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PU1 | A consensus score reads as credible at a glance (not as another fake review count) | A | **Medium** | Pretotype screens; 5-user trust interviews |
| PU2 | Receipts (short quotes/clips with timestamps) give enough context to convince without full videos | B | **Medium** | Same pretotype sessions |

### Viability

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PB1 | Affiliate revenue survives the creator-link conflict — users transact via *our* links even though creators push their own | All | **Low-Medium** | Live affiliate links in concierge/content; measure CTR |
| PB2 | Mining creator content and displaying names/quotes/clips commercially survives platform ToS (YouTube API storage/derivative-use limits) and publicity-rights scrutiny | F, B | **Low-Medium** | Legal opinion + YouTube API ToS review **before** pipeline build |
| PB3 | Creator backlash is manageable — creators won't takedown-storm or mobilize audiences against an app monetizing their recommendations | All | **Low-Medium** | Outreach interviews with 5–10 creators; gauge reaction; design opt-in/opt-out posture |
| PB4 | Pipeline costs (transcripts + LLM extraction at catalog scale) fit a small-team budget | F | **Medium** | Cost-per-video measured in the extraction spike, extrapolated |

### Feasibility

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PF1 | LLM extraction reliably separates **endorse / mention / criticize** for product references in creator content | F | **Medium** | Spike: 50 videos, hand-labeled ground truth, precision/recall target ≥90/80 |
| PF2 | Sponsorship detection is accurate enough to publish — disclosed is easy; *undisclosed* is hard, and a wrong "unsponsored" label is a trust and defamation hazard | F, A | **Low-Medium** | Same spike; consider "no disclosure found" framing instead of "unsponsored" |
| PF3 | Entity resolution maps spoken/nicknamed product references to SKUs+INCI at high accuracy | F | **Medium** | Same spike; measure resolution rate |
| PF4 | Enough creator-content **density** exists per concern to form meaningful consensus — *per candidate market* (India's YouTube skincare corpus vs global English) | F, A | **Medium** | Content-density audit in both markets — doubles as the market-choice input |
| PF5 | Endorsement freshness is maintainable (creators change routines; products reformulate) | F | **Medium** | Defer to build; design decay into the graph schema |

### Ethics

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PE1 | Amplifying creator consensus won't amplify harmful trends (consensus ≠ safety) — the ingredient pillar + derm rules catch what the crowd gets wrong | A | **Medium** | Derm review of consensus routines (same panel as PV4) |
| PE2 | Publicly labeling content sponsored/unsponsored is accurate and fair enough to publish responsibly | A | **Low-Medium** | Editorial standard + legal framing review (with PF2) |
| PE3 | Using creators' names/likenesses to drive affiliate sales without consent is defensible *ethically*, not just legally — or an opt-out/opt-in posture is needed | All | **Medium** | Creator outreach (with PB3) informs the posture |

### Go-to-Market

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PG1 | Search/social demand exists for consensus-style queries ("best acne serum according to derms", "is X sponsored") | All | **Medium-High** | Keyword volume research; content test CTR |
| PG2 | Creators are a usable channel (or at least neutral) rather than an adversary — some will amplify "receipts" content | All | **Low-Medium** | Same creator outreach; offer early looks |
| PG3 | A clear beachhead exists between **India** (thin creator corpus, weak affiliate rates, no direct competitor) and **global English** (dense corpus, strong affiliate, LTK/ShopMy adjacency) | All | **Unknown** | PF4 density audit + parallel demand funnels decide it with data |

### Strategy & Objectives

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PS1 | The endorsement graph compounds into a moat before platforms or incumbents replicate it | F | **Medium** | Not directly testable; mitigate via speed + graph depth |
| PS2 | YouTube dependency is survivable (API/policy change doesn't kill the pipeline) | F | **Medium** | Architecture hedge: multi-source design, cached derivatives |
| PS3 | A small team can dig **two moats at once** (INCI DB + endorsement graph) without fatal focus-splitting | F | **Low-Medium** | Honest scope/capacity review after both spikes price the work |
| PS4 | "Consensus, verified by ingredients" is meaningfully differentiated from creator storefronts (LTK/Wishlink), community apps (Picky), and plain YouTube search | All | **Medium** | Positioning test in the demand funnel |

### Team

| ID | Assumption | Bets | Confidence | Candidate test |
|----|-----------|------|------------|----------------|
| PT1 | Team can cover NLP/data-pipeline work on top of the consumer app + content + ingredient DB | All | **Unknown** | Skills inventory after spikes size the work |
| PT2 | Derm advisors recruitable (carried from original map — now also needed to review consensus routines) | A | **Medium** | Outreach to 5 derms |

---

## Cross-cutting observations

1. **The pivot's deepest risk is PV1** — the entire concept presumes parasocial trust aggregates. If people only trust *their* creator, consensus is a feature nobody asked for.
2. **The data source is also the adversary** (PB2 + PB3 + PG2): the product mines creators' content, intercepts their affiliate economics, and then needs their goodwill. This tension needs a designed posture (attribution-forward, opt-out honored, maybe rev-share later) before build.
3. **Foundations doubled, team didn't** (PS3): the original plan had one moat to dig; the pivot has two. Scope risk is now a first-class assumption.
4. **The extraction spike is the F1-equivalent**: cheap, fast, and existential — and PF4's density audit doubles as the market-selection instrument, answering the reopened India-vs-global question with data instead of debate.
