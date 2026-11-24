# Comments Reviews

> Category: Communication & Social

## Purpose
User-generated feedback threads with ratings.

## Key Elements
- Summary header: average rating, count, star-distribution histogram
- Review cards: stars, author, date, text, helpful-vote button
- Write-review CTA; sort (recent/top) and filter (rating, verified)
- Report/flag action per item

## States & Variations
- No reviews yet ("be the first")
- User's own review pinned with edit/delete
- Pending moderation / removed content placeholder
- Threaded replies (comments) vs flat reviews

## Design Notes
- The distribution histogram builds more trust than the average alone
- Verified-purchase/verified-user badges materially change credibility
- Ask for reviews at the right moment (after successful use), and make writing fast: stars first, text optional

## Technical Considerations
- Moderation pipeline is the real work: automated filters (spam, profanity, PII) + manual review queue + appeal path; plan it before launch, not after the first incident
- Enforce one review per user per item server-side; edits keep history if disputes matter
- Helpful votes: dedup per user, recompute ranking asynchronously
- Aggregate rating cached and updated on write — don't compute averages on read at scale
- Sort/filter/pagination server-side; report actions hide content locally immediately regardless of backend outcome
- Legal: UGC means you need takedown handling and terms coverage

## References
- App Store reviews, Amazon review sections (Mobbin)
