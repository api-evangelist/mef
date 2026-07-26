---
name: Subscribe to LSO events
description: Register a listener with a Seller's LSO API hub, receive the TM Forum-style event callbacks, and tear the subscription down cleanly.
api: openapi/mef-lso-sonata-product-order-management-openapi.yml
apis:
  - openapi/mef-lso-sonata-product-order-management-openapi.yml
  - openapi/mef-lso-sonata-product-order-notification-openapi.yml
  - openapi/mef-lso-sonata-quote-notification-openapi.yml
  - openapi/mef-lso-legato-service-ordering-notification-openapi.yml
operations:
  - registerListener
  - retrieveHub
  - retrieveEventSubscription
  - unregisterListener
  - productOrderStateChangeEvent
  - productOrderItemStateChangeEvent
  - productOrderItemExpectedCompletionDateSetEvent
  - listenToQuoteStateChangeEvent
  - listenToQuoteItemStateChangeEvent
generated: '2026-07-25'
method: generated
---

# Subscribe to LSO events

Every LSO functional area ships as a **pair**: a Management API you call, and a Notification API
that describes the callbacks the Seller makes to you. 39 of the 94 published documents are
notification definitions. This is a hub/listener pattern inherited from the TM Forum Open APIs —
there are no polling webhooks and no signed-payload scheme defined at the standard level.

## Steps

1. **Stand up a listener endpoint** that implements the paths in the paired Notification API for
   the events you care about, e.g. `POST /listener/productOrderStateChangeEvent`,
   `POST /listener/productOrderItemStateChangeEvent`,
   `POST /listener/productOrderItemExpectedCompletionDateSetEvent`. The operationIds in that
   document are the exact event names.
2. **Register.** `registerListener` — POST `/hub` on the *management* API with
   `{"callback": "https://your.host/lso/callbacks", "query": "<optional filter>"}`. The response
   carries the subscription `id`.
3. **Confirm.** `retrieveHub` (GET `/hub/{id}`) — on the Service Ordering APIs the same operation is
   named `retrieveEventSubscription`. Store the id; it is the only handle you get.
4. **Receive and acknowledge.** Return 2xx quickly and process asynchronously. Events carry the
   resource id — re-read the resource (`retrieveProductOrder`, `retrieveQuote`, …) rather than
   trusting the event body as a complete state.
5. **Deregister** when the integration is retired: `unregisterListener` (DELETE `/hub/{id}`).

## Rules

- **Register one hub per functional area.** The hub on the Product Order API delivers only product
  order events; quotes, trouble tickets, alarms and inventory each have their own hub.
- **Authorise the callbacks.** In the security variant of each document, every listener operation
  carries its own OAuth scope (`productOrderStateChangeEvent`, `listenToQuoteStateChangeEvent`, …).
  The Seller calls you — agree the credential direction during onboarding; the standard does not fix it.
- **Expect at-least-once semantics and no ordering guarantee.** There is no idempotency key
  anywhere in LSO; de-duplicate on `(resource id, state, event time)` yourself.
- Full event catalog with counts per document: `asyncapi/mef-webhooks.yml`. For continuous
  performance data, prefer the streaming surface (AsyncAPI 2.0.0) over event callbacks.
