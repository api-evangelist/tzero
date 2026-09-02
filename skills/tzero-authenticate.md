---
name: Authenticate against the tZERO API
description: Exchange tZERO-issued credentials for a bearer token and keep it fresh for the one-hour lifetime.
api: openapi/tzero-issuance-secondary-markets-openapi.json
operations: [loginUsingPOST, refreshTokenUsingPOST]
generated: '2026-09-01'
method: generated
source: https://apidocs.tzero.com/docs
---

# Authenticate against the tZERO API

Every call to the tZERO Issuance & Secondary Markets API needs **two** credentials, not one.

## Before you start

tZERO issues all three values (`API key`, `clientId`, `clientSecret`) — there is no self-serve
signup for API credentials. The docs say plainly: *"x-apikey — Contact us to get your API key."*
Base URL: `https://gateway-web-api.tzero.com/app`.

## Steps

1. **Mint an access token** — `loginUsingPOST` (`POST /auth/v1/api/token`).
   Send header `x-apikey: <YOUR_API_KEY>` and a JSON body `{"clientId": "...", "clientSecret": "..."}`.
   The response carries an `accessToken` that is valid for **1 hour**.
2. **Send both credentials on every subsequent request** — `x-apikey` *and*
   `Authorization: Bearer <accessToken>`. Sending only one returns `401 Unauthorized`.
3. **Refresh before expiry** — `refreshTokenUsingPOST` (`POST /auth/v1/api/refresh`) using the
   `refreshToken` header. Do not re-run step 1 on every call; the login endpoint is not a per-request
   operation.

## Rules

- A `401` means the token is missing, malformed or expired. A `403` means the caller is
  authenticated but has no access to the account or user in the path — refreshing will not fix it.
- No rate limits are published (`rate-limits/tzero-rate-limits.yml`), so there is no
  `Retry-After` to obey. Back off conservatively on 5xx and `502 Bad Gateway`, which the contract
  uses for downstream service failures.
- The Institutional API (`api.t0direct.com`) is a **separate** surface with a different scheme:
  a single scoped `X-API-Key` header, no token exchange. Do not reuse credentials across the two.
