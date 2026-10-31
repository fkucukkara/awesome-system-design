# API Design

The API is the contract that drives your high-level design. Derive it from functional requirements.

## Style choice

| Style | When |
|---|---|
| REST | Default for client-facing APIs |
| GraphQL | Many client types with different data shapes |
| gRPC | Internal service-to-service, streaming, strict schemas |

## REST rules of thumb

- Plural nouns for resources: `POST /v1/tweets`, `GET /v1/tweets/{id}`.
- Verbs map to HTTP methods. `GET` safe and idempotent; `PUT`/`DELETE` idempotent; `POST` not by default.
- The caller identity comes from the **auth token**. Never accept `userId` in the body for authorization.
- Version in the path (`/v1`) or header; never break existing clients silently.

## Pagination

| Type | Pros | Cons |
|---|---|---|
| Offset/limit | Simple, jump to page N | Slow on deep pages, unstable under writes |
| Cursor/keyset | Stable, index-friendly | No random access |

Prefer cursor pagination for feeds and large lists:

```
GET /v1/feed?limit=20&cursor=eyJ0cyI6...
-> { "items": [...], "nextCursor": "..." }
```

## Idempotency and safety

- Mutating calls that can be retried take an `Idempotency-Key` header; the server stores the result for a TTL.
- Use optimistic concurrency (`ETag` / `If-Match` or a `version` field) for updates.
- Return `429` with `Retry-After` for rate limits; `202` plus a status resource for long-running work.

## Large payloads

Avoid proxying big files through your API tier. Return a **presigned URL** and let the client upload/download directly to object storage.

## Real-time

Define the core request/response API first. Add WebSocket/SSE message schemas separately, with ack and sequence numbers.

## Gotchas

- Chatty APIs increase latency; provide batch endpoints or composite views for mobile.
- Do not leak internal IDs that are guessable if authorization is weak; check ownership on every read.
- Error contract: stable machine-readable codes, not just messages.
