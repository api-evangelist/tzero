---
name: Trade on the tZERO ATS
description: Price, place, monitor and cancel secondary-market orders against the tZERO Alternative Trading System.
api: openapi/tzero-issuance-secondary-markets-openapi.json
operations: [getMarketSchedules, getOrderFee, createOrder, getOrders, getOrder, cancelOrder, getAccountBalance]
generated: '2026-09-01'
method: generated
source: https://apidocs.tzero.com/docs/explorer
---

# Trade on the tZERO ATS

## Steps

1. **Check the session** — `getMarketSchedules` (`GET /markets/v1/schedules`) returns pre-market,
   regular and post-market windows. As of 2025-12-15 the ATS accepts order entry 24/7 and trades
   23.5 hours on business days (12:05am–11:35pm ET, Mon–Fri, excluding market holidays), so "the
   market is closed" is no longer a safe default assumption — read the schedule.
2. **Look at the book** — `GET /markets/v1/mdt/public-snapshots/{symbol}` and
   `GET /markets/v1/mdt/public-pricehistory/{symbol}` (declared without operationIds; address by path).
3. **Price the fee first** — `getOrderFee` (`GET /trading/v1/fee`). tZERO publishes no rate card for
   API trading, so this endpoint is the only reliable pre-trade cost signal. Treat it as the dry-run.
4. **Place the order** — `createOrder` (`POST /trading/v1/accounts/{accountId}/orders`) with a
   client-supplied `transactionId` for idempotency and tracing.
5. **Monitor** — `getOrders` and `getOrder`.
6. **Cancel** — `cancelOrder` (`DELETE /trading/v1/accounts/{accountId}/orders/{orderId}`).

## Reversibility

`cancelOrder` is the reversal path for `createOrder`. It works only while the order is still
cancellable; past that point tZERO returns **HTTP 422 "Order cannot be cancelled"**. There is no
unwind for a filled order through this API. An agent must therefore treat a `201` from `createOrder`
as potentially final and confirm cancellability before assuming it can retract.

## Retries

Retry a `createOrder` **only** with the identical `transactionId`. A new `transactionId` on a retry is
a new order, not a retry — this is the single most expensive mistake available on this surface.

## Low-latency alternative

For order entry, drop-copy execution reports and streaming market data, tZERO publishes FIX 4.2 and
FIX 4.4 specifications instead of REST: https://apidocs.tzero.com/docs/fix
