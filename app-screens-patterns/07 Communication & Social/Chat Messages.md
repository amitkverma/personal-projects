# Chat Messages

> Category: Communication & Social

## Purpose
Conversation list plus message thread with composer.

## Key Elements
- Conversation list: avatar, name, last-message preview, timestamp, unread badge
- Thread: message bubbles (sent/received), day separators, timestamps, read receipts
- Typing indicator
- Composer: text input, attachments, send; grows with content

## States & Variations
- Message lifecycle: sending → sent → delivered → read → failed (retry affordance)
- Offline: queued messages marked as pending
- Deleted/edited messages; blocked or reported user
- Group threads (names + avatars per message)

## Design Notes
- Optimistic send — the bubble appears the instant Send is tapped
- Failed sends must be visibly retryable in place, not silently dropped
- Keep the composer glued above the keyboard through every transition; broken keyboard handling ruins chat UX

## Technical Considerations
- Real-time transport: WebSocket or a managed layer (Firestore, Stream, Sendbird); handle reconnect with backfill of missed messages
- Client-generated message UUIDs enable optimistic rendering, dedup on server echo, and retry idempotency
- Order by server timestamp, not client clock; resolve near-ties deterministically
- Local message store for instant history load and an offline outbox with background retry
- Inverted list rendering with dynamic cell heights is notoriously fiddly — budget time or use a proven chat UI kit
- Push integration: thread deep links, inline reply actions, and unread-count sync (server-authoritative)
- Decide encryption and retention policy early — retrofitting E2E encryption is a rewrite

## References
- WhatsApp, iMessage as canonical patterns (Mobbin)
