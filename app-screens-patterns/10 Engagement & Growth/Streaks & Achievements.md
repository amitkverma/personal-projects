# Streaks & Achievements

> Category: Engagement & Growth

## Purpose
Habit-forming progress, badges, and leaderboards.

## Key Elements
- Streak counter with calendar heat-view or flame icon
- Badge grid: earned (full color) vs locked (silhouette + criteria)
- Progress bar toward the next tier
- Unlock celebration; shareable achievement card
- Optional leaderboard among friends

## States & Variations
- Active streak / at-risk today (drives the reminder notification) / broken
- Streak-freeze or repair mechanic
- Badge tiers (bronze/silver/gold); seasonal or event badges

## Design Notes
- Show locked badges with explicit criteria — the goal-gradient effect does the motivating
- A streak-repair mechanic (freeze, one-day grace) prevents the rage-quit that follows a broken 60-day streak
- Gamification must decorate the core loop, not replace it; if users log to keep a number alive, the number owns you

## Technical Considerations
- Compute streaks server-side: client clocks are wrong and manipulable, and users cross timezones — define the day boundary rule (user's home tz? current tz? UTC?) explicitly and apply it consistently everywhere
- Achievement awards must be idempotent events (no double unlocks from sync retries) in an append-only log
- Handle offline backfill: an entry logged offline yesterday and synced today must count for yesterday's streak
- Schedule at-risk streak reminders relative to each user's typical active hour, not a global time
- Load badge art from a versioned remote catalog so new badges ship without app releases
- Leaderboards need privacy controls (opt-in, display-name rules)

## References
- Duolingo streaks (the canonical implementation); Headspace run streaks (Mobbin)
