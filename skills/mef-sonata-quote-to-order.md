---
name: LSO Sonata quote-to-order
description: Run the inter-provider buy path across MEF/Mplify LSO Sonata — validate the address, qualify the product offering, request a quote, then place and track the product order.
api: openapi/mef-lso-sonata-product-order-management-openapi.yml
apis:
  - openapi/mef-lso-sonata-geographic-address-management-openapi.yml
  - openapi/mef-lso-sonata-product-offering-qualification-management-openapi.yml
  - openapi/mef-lso-sonata-quote-management-openapi.yml
  - openapi/mef-lso-sonata-product-order-management-openapi.yml
  - openapi/mef-lso-sonata-product-inventory-management-openapi.yml
operations:
  - createGeographicAddressValidation
  - retrieveGeographicAddressValidation
  - createProductOfferingQualification
  - retrieveProductOfferingQualification
  - createQuote
  - retrieveQuote
  - declineQuote
  - createProductOrder
  - retrieveProductOrder
  - listCharge
  - patchCharge
  - registerListener
  - listProduct
generated: '2026-07-25'
method: generated
---

# LSO Sonata quote-to-order

You are acting as the **Buyer** — a Service Provider buying wholesale connectivity from
another Service Provider (the **Seller**) over the LSO Sonata Interface Reference Point.
Mplify (formerly MEF) defines the contract; the Seller hosts it at
`https://{serverBase}/mefApi/sonata/<api>/v<major>/`.

## Before you start

- Auth is OAuth 2.0 **client credentials**, machine-to-machine. Each operation has its own
  scope, named after the operationId (`createProductOrder`, `listQuote`, …). See
  `scopes/mef-scopes.yml` and `authentication/mef-authentication.yml`.
- Almost every call carries **`buyerId` and `sellerId`** query parameters. Set both on every request.
- There is **no idempotency key** in this API. Use your own `externalId` on the Buyer side and
  check with a list call before re-submitting a create.

## Steps

1. **Validate the service address.** `createGeographicAddressValidation` (POST
   `/geographicAddressValidation`). The result may come back asynchronously — poll
   `retrieveGeographicAddressValidation` until the state settles, or register for
   `listenToGeographicAddressValidationStateChangeEvent`. Carry the returned
   `geographicAddress.id` forward; do not re-key the address by hand.
2. **Qualify the offering.** `createProductOfferingQualification` (POST
   `/productOfferingQualification`) with the validated address and the product specification you
   intend to buy. Poll `retrieveProductOfferingQualification`. A qualification that comes back
   unqualified ends the flow — do not proceed to quote.
3. **Browse what is buyable** (optional). `listProductOffering` / `retrieveProductOffering` and
   `listProductSpecification` in the Product Catalog API tell you what the Seller sells and with
   which characteristics.
4. **Request a quote.** `createQuote` (POST `/quote`), referencing the qualification. Poll
   `retrieveQuote`. Use `declineQuote` if the price is unacceptable and `cancelQuote` to withdraw
   the request; both are POSTs to their own paths, not state PATCHes.
5. **Place the order.** `createProductOrder` (POST `/productOrder`) referencing the accepted quote.
   Poll `retrieveProductOrder`, or better, `registerListener` (POST `/hub`) so the Seller pushes
   `productOrderStateChangeEvent`, `productOrderItemStateChangeEvent` and
   `productOrderItemExpectedCompletionDateSetEvent` to your callback.
6. **Handle charges.** If the Seller raises a charge, it appears via `listCharge` /
   `retrieveCharge`; you respond with `patchCharge`. An unanswered charge blocks the order.
7. **Adjust or cancel.** `createModifyProductOrderItemRequestedDeliveryDate` moves a requested
   date; `createCancelProductOrder` requests cancellation. Both are *requests* the Seller may
   refuse — always read back the returned state.
8. **Confirm delivery.** When the order completes, the delivered product appears in Product
   Inventory: `listProduct` / `retrieveProduct`.

## Rules

- **Poll with pagination discipline.** List operations take `offset`/`limit` and return
  `X-Total-Count`, `X-Result-Count` and `X-Pagination-Throttled`. If `X-Pagination-Throttled` is
  `true`, narrow the filter (`orderDate.gt` / `orderDate.lt`) rather than paging blindly.
- **Read the error `code`, not just the status.** `422 tooManyRecords` means narrow the query;
  `422 referenceNotFound` means an id you passed does not exist on the Seller side;
  `501 notImplemented` means the Seller does not support that optional operation — degrade, do not
  retry. Full catalog: `errors/mef-problem-types.yml`.
- **Never invent a Seller endpoint.** `{serverBase}` is a template variable; it comes from the
  commercial onboarding with that Seller, not from Mplify.
