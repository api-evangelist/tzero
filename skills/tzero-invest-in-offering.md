---
name: Invest in a tZERO primary offering
description: Browse assets, create and sign an investment, fund it by wire, and cancel while it is still cancellable.
api: openapi/tzero-issuance-secondary-markets-openapi.json
operations: [createInvestment, updateInvestment, signInvestmentAgreement, addInvestmentPayment, submitInvestment, getWireInstructions, getInvestmentsByAccount, cancelInvestment, addBankAccount, getBankAccounts, transfer, getAccountBalance]
generated: '2026-09-01'
method: generated
source: https://apidocs.tzero.com/docs/explorer
---

# Invest in a tZERO primary offering

Assumes a KYC-cleared account (see `tzero-onboard-investor`).

## Steps

1. **List what is open** — `GET /pi/v1/assets` (no operationId is declared for this path in the
   published contract; address it by method + path).
2. **Create the investment** — `createInvestment`
   (`POST /pi/v1/assets/{assetId}/investments`). Supply a client-generated `transactionId`; it is
   **required, non-blank** and is the idempotency key for this surface.
3. **Sign the agreement** — `signInvestmentAgreement`
   (`POST /pi/v1/assets/{assetId}/investments/{investmentId}/agreement`). The signature name must
   match the account holder (`SIGNATURE_NAME_MISMATCH`) and an MSA `version` is required.
4. **Fund it.** Either link a bank account (`addBankAccount`, then `transfer`) or pull wire
   instructions with `getWireInstructions`
   (`GET /pi/v1/docs/assets/{assetId}/accounts/{accountId}/wire-instructions`). Only `WIRE` is
   supported as a payment type (`PAYMENT_TYPE_NOT_SUPPORTED`). Record the payment with
   `addInvestmentPayment`.
5. **Submit** — `submitInvestment` (`POST /pi/v1/investments/{investmentId}/submit`).
6. **Verify** — `getInvestmentsByAccount` and `getAccountBalance`.

## Idempotency

Reuse the **same** `transactionId` when you retry a create/update/submit/cancel. Omitting it returns
`TRANSACTION_ID_REQUIRED`. There is no `Idempotency-Key` header on this surface — the key travels in
the body.

## Reversibility — know this before you submit

`cancelInvestment` (`DELETE /pi/v1/investments/{investmentId}`) is the only undo. It works until the
investment reaches a status that can no longer be canceled, at which point tZERO returns
`INVESTMENT_CANNOT_BE_CANCELLED` — *"This investment can no longer be canceled."* tZERO publishes no
time-based window; the gate is status, not a clock. Check cancellability before you fund, not after.

## Offering-type rules

Reg CF assets require `REG_CF_TERMS_NOT_ACCEPTED` to be satisfied; sending Reg CF terms on a non-Reg-CF
asset is itself an error (`REG_CF_TERMS_ONLY_APPLICABLE_TO_REG_CF`). `ASSET_NOT_OPEN` means the offering
is closed regardless of everything else.
