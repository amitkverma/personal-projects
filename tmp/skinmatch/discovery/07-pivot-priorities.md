# SkinMatch PIVOT — Assumption Prioritization (Impact × Risk)

**Date:** 23 July 2026
**Input:** 24 new/changed assumptions from `06-pivot-assumptions.md`
**Frame:** Build/kill reopened — priority to assumptions that, if false, mean *don't build the pivot* (or *build it differently*). Ingredient-pillar priorities in `03-assumption-priorities.md` still stand.

## 🔴 High Impact × High Risk → TEST (leap-of-faith clusters)

| Rank | Cluster | IDs | Why leap-of-faith | Test effort |
|------|---------|-----|-------------------|-------------|
| **1** | **Extraction & Density Spike** — can we mine reliable endorsements at all, and is there enough content per market? | PF1, PF2, PF3, PF4, PB4 (→ answers PG3 market choice, prices PS3) | The pivot's F1-equivalent. If extraction can't separate endorse/mention/criticize, the graph is poison; if density is thin in a market, consensus doesn't exist there. Doubles as the **market-selection instrument** | Medium (~1 week, mostly LLM eval work) |
| **2** | **Creator Posture** — legality and backlash | PB2, PB3, PE3, PG2 | The data source is also the adversary. A ToS/publicity-rights wall or creator revolt kills the concept regardless of demand. Also the cheapest cluster to start | Low (legal review + 5–10 outreach conversations) |
| **3** | **Consensus Value** — does anyone want an aggregate? | PV1, PV2, PV5, PS4 (+ free reads on PG1) | The deepest product risk: parasocial trust may not transfer to a number. Everything user-facing presumes it does | Low-Medium (demand funnel with framing A/Bs, 2 weeks elapsed) |
| **4** | **Routine Quality & Swaps** — is the output good, and will users accept substitutions? | PV4, PE1, PV3 | Consensus routines could be derm-disapproved trend-stacks; and if influencer-driven buyers reject dupe swaps, the pillar synthesis (the differentiator) fails | Medium (derm panel + concierge test; needs Cluster 1 sample data) |
| **5** | **Economics & Scope Reality** | PB1, PS3, PT1 | Creator-link conflict may starve affiliate revenue; and two moats with one team is a scope bet that needs pricing, not optimism | Low (live links piggyback + capacity review after spikes) |

## 🟡 High Impact × Lower Risk → PROCEED with monitoring

| IDs | Assumption | Action |
|-----|-----------|--------|
| PG1 | Search demand for consensus-style queries | Keyword research inside Cluster 3; high prior confidence |
| PU1, PU2 | Score credibility + receipts comprehension | Fold into Cluster 4 concierge sessions as observation goals |
| PS2 | YouTube dependency survivable | Architecture decision: multi-source design, cache derivatives — handle at build |
| PT2 | Derm advisors recruitable | Same outreach as Cluster 4's panel; reuse |

## ⚪ Defer

| IDs | Assumption | Why |
|-----|-----------|-----|
| PV6 | Receipts/Trend radar drive return visits | Retention — untestable pre-launch |
| PF5 | Freshness maintainable | Build-phase schema decision (design decay in from day one) |
| PS1 | Graph compounds into a moat | Consequence of speed, not a testable input |

## Sequencing logic

- **Cluster 1 and Cluster 2 start immediately and in parallel** — one is a technical spike, the other is legal desk work + conversations; between them they cover both existential axes (can we? may we?).
- **Cluster 3** (demand funnel) starts week 1 too — content needs time to accumulate signal. Run it market-agnostic in English first; Cluster 1's density audit then tells us where to focus paid amplification.
- **Cluster 4** waits for Cluster 1's sample output (real consensus data for the concierge routines; hand-mining 20 videos is the fallback).
- **Cluster 5** piggybacks throughout and concludes with a scope/capacity review once the spikes have priced the foundations.

## Relationship to the ingredient-pillar priorities (03)

The original clusters remain valid but re-rank: the **INCI data audit (old Cluster 1)** stays P0 — it now also feeds entity resolution and budget swaps. The **dupe value chain (old Cluster 3)** partially merges into Cluster 4 here (swap acceptance). The **sensitive-skin interviews (old Cluster 5)** drop to P2 for the pivot — sensitivity filtering is now a supporting check, not the lead promise.
