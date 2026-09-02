---
name: Onboard an investor and clear KYC
description: Create an individual broker-dealer account on tZERO, trigger KYC, and read the result before letting the investor transact.
api: openapi/tzero-issuance-secondary-markets-openapi.json
operations: [onboardIndividualAccount, getAccountById, updateInvestor, triggerKyc, getUserKycStatus, addTrustedContact, patchFinancialInfo]
generated: '2026-09-01'
method: generated
source: https://apidocs.tzero.com/docs/explorer
---

# Onboard an investor and clear KYC

Nothing else on tZERO works until an account exists and KYC has cleared. Run this first.

## Steps

1. **Create the account** — `onboardIndividualAccount` (`POST /pi/v1/accounts/individual`).
   Returns the `accountId` and `userId` you will carry through every later call.
2. **Trigger KYC** — `triggerKyc` (`POST /pi/v1/users/{userId}/kyc`).
3. **Poll the result** — `getUserKycStatus` (`GET /pi/v1/users/{userId}/kyc`). Do not proceed to
   investment or trading until this reports a cleared state.
4. **Fill in what is required for the offering type** — `patchFinancialInfo`
   (`PATCH /pi/v1/accounts/{accountId}/users/{userId}/financialInfo`). Annual income and net worth
   are **required** for Reg A and Reg CF investments (`ANNUAL_INCOME_REQUIRED`, `NET_WORTH_REQUIRED`).
5. **Optional** — `addTrustedContact` (`POST /pi/v1/accounts/{accountId}/trustedContact`).
6. **Read back** — `getAccountById` (`GET /pi/v1/accounts/{accountId}`).

## Validation rules that will bite you

These are published codes from the contract's `x-businessValidationErrorCodes` — the full registry
is in `errors/tzero-error-codes.yml`.

- **Age and DOB** — `INVESTOR_AGE_INSUFFICIENT` (must be 18+), `DATE_OF_BIRTH_IN_FUTURE`,
  `DOB_NOT_ALLOWED` (no more than 120 years in the past).
- **Jurisdiction** — `JURISDICTION_COUNTRY_NOT_ALLOWED` comes back as **HTTP 422**, not 400.
  `JURISDICTION_STATE_REQUIRED_FOR_US` and `JURISDICTION_STATE_FORMAT_INVALID` (two-character code)
  apply whenever the country is US.
- **Identifiers** — `TAX_COUNTRY_MUST_BE_US` when the address or citizenship is US;
  `PASSPORT_REQUIRED_FOR_NON_US` for a non-US physical address; country codes must be two-letter ISO.
  You cannot delete the last identifier (`GOVERNMENT_IDENTIFIER_AT_LEAST_ONE_REQUIRED`).

## Error handling

Errors arrive as `{"errors":[{"code","message","field","details"}]}` — `field` is a JSON path such
as `investor.dateOfBirth`, so map failures back to your form fields from `field`, not from `message`.
