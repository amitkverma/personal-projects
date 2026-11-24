# Onboarding Quiz

> Category: Launch & Onboarding

## Purpose
Short personalization questions (goals, preferences) used to tailor content and recommendations.

## Key Elements
- Progress indicator (bar or step count)
- One question per screen, selectable chips or cards
- Continue button (or auto-advance on single-select)
- A "payoff" screen: recommendation or plan derived from answers

## States & Variations
- Single-select (auto-advance) vs multi-select (explicit continue)
- Skippable vs required questions
- "Building your plan…" interstitial before the payoff
- Branching: later questions depend on earlier answers

## Design Notes
- 3–7 questions is the sweet spot; every extra screen costs completion rate
- Explain why you ask when a question feels personal — trust drives honesty
- Show the personalization payoff immediately (e.g. "For Calm Explorers like you" à la Headspace)
- Let users change answers later in settings

## Technical Considerations
- Model answers as a versioned schema — questions will change across releases and old answers must still parse
- Store answers locally until an account exists, then sync; handle anonymous-to-registered identity merge
- Drive the question list from server config so product/marketing can iterate without app releases
- Preserve answers on back-navigation and process death (draft state)
- Feed answers into the recommendation engine through one documented API, not ad-hoc flags
- Funnel analytics per question to find abandonment points

## References
- Headspace "What's on your mind?" / mindfulness-style quiz (Mobbin)
- Flo goal selection, Noom-style long quizzes (upper bound example)
