# Help & Support

> Category: Profile & Settings

## Purpose
FAQ, contact options, and troubleshooting resources.

## Key Elements
- Search across help articles
- Top articles; categorized topics
- Contact routes: chat, email/ticket — with expected response times
- Article view with helpful-yes/no feedback

## States & Variations
- Search with no results → escalate-to-contact path
- Ticket submitted confirmation with reference number
- Live chat active/queued; offline (cached top articles)

## Design Notes
- Good search deflects tickets, but never hide the contact option behind mandatory article-reading
- State response times honestly; a met 48h expectation beats a missed 2h promise
- Contextual entry points (help icon on a failing screen → the relevant article) beat a generic hub

## Technical Considerations
- Back articles with a CMS/helpdesk (Zendesk, Intercom, or headless CMS); cache top articles for offline
- Pre-fill support requests with app version, OS, device model, user ID, and recent error codes (with user consent) — this halves resolution time
- In-app chat SDKs add real binary size and background behavior; evaluate against a simple ticket form
- Deep-link individual articles so error states can link directly to their fix
- Track search-with-no-results and article-unhelpful votes — that's the content backlog

## References
- Intercom/Zendesk mobile patterns
