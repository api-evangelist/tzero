---
name: Declare dividends, corporate actions and votes on the tZERO Institutional API
description: Submit review-gated transfer-agent declarations with the required Idempotency-Key header, then track them to execution over webhooks.
api: openapi/tzero-institutional-openapi.json
operations: ['POST /api/v1/dividends', 'GET /api/v1/dividends/{id}', 'GET /api/v1/dividends/{id}/funding', 'GET /api/v1/dividends/{id}/reconciliation', 'POST /api/v1/dividends/{id}/cancel', 'POST /api/v1/corporate-actions', 'POST /api/v1/corporate-actions/{id}/cancel', 'POST /api/v1/proposals', 'GET /api/v1/proposals/{id}/results', 'POST /api/v1/webhooks/']
generated: '2026-09-01'
method: generated
source: https://api.t0direct.com/api/v1/openapi.json
---

# Declare dividends, corporate actions and votes (tZERO Institutional API)

Base URL `https://api.t0direct.com/api/v1`. Auth is a single scoped `X-API-Key` header — **not** the
bearer-token flow used by the Issuance & Secondary Markets API. The published contract declares no
`operationId`s, so address every operation by method + path exactly as written above.

## Scopes

`TA_WRITE` is required to declare; `TA_READ` to read back. A request whose key lacks the required
scope returns **403 FORBIDDEN**. `FULL_ACCESS` satisfies every scope — the contract itself says to
use it sparingly.

## Steps

1. **Subscribe to events first** — `POST /api/v1/webhooks/` with an HTTPS `url` and an `events` array.
   The secret is returned **once** on creation; store it, and verify every payload with HMAC-SHA256.
   Send yourself a `ta.test` with `POST /api/v1/webhooks/{id}/test` before relying on it.
2. **Declare** — `POST /api/v1/dividends`, `/api/v1/corporate-actions` or `/api/v1/proposals`.
   Every one of these mutations **requires an `Idempotency-Key` header.**
3. **Wait for review.** Declarations enter `PENDING_REVIEW`; a tZERO transfer-agent reviewer approves
   or rejects each one under an SEC Rule 17Ad-2 turnaround timer. This is not an API latency problem
   to poll aggressively around — track it with the `ta.dividend.*`, `ta.corporate_action.*` and
   `ta.proposal.*` webhook families.
4. **Fund a cash dividend** — `GET /api/v1/dividends/{id}/funding` returns USDC deposit instructions.
5. **Reconcile** — `GET /api/v1/dividends/{id}/reconciliation` compares declared against distributed;
   `GET /api/v1/proposals/{id}/results` returns final tallies with on-chain anchors.

## Idempotency rules

- An **exact** retry with the same `Idempotency-Key` replays the original response.
- Reusing a key with a **different payload** returns **409 Conflict**. Generate one key per logical
  declaration and never recycle.
- Transfers and issuances use a different mechanism: an `idempotencyKey` **field in the body**, where
  a duplicate returns the original record.

## Reversibility

Each of the three entities exposes `POST .../{id}/cancel`. tZERO does not publish the point after
execution at which cancel stops working, so do not assume a post-execution undo exists. On-chain
executions (dividend creation on the claim contract, split initialization, vote anchoring) settle via
tZERO's Fireblocks custody and surface transaction hashes on the entity — once anchored, they are not
retractable through this API.

## What this API cannot do

Investors vote in their own t0kenizer portal accounts. **Ballots cannot be submitted through this
API** — the contract states this explicitly. Do not build a voting client against it.
