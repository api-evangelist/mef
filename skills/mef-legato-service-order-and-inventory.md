---
name: LSO Legato service order and inventory
description: Drive intra-provider service fulfilment — place a service order from a business application into the Service Orchestration Functionality and reconcile the result against service inventory.
api: openapi/mef-lso-legato-service-ordering-management-openapi.yml
apis:
  - openapi/mef-lso-legato-service-ordering-management-openapi.yml
  - openapi/mef-lso-legato-service-ordering-notification-openapi.yml
  - openapi/mef-lso-legato-service-inventory-management-openapi.yml
  - openapi/mef-lso-legato-service-inventory-notification-openapi.yml
operations:
  - createServiceOrder
  - listServiceOrder
  - retrieveServiceOrder
  - registerListener
  - retrieveEventSubscription
  - unregisterListener
  - serviceFind
  - serviceGet
generated: '2026-07-25'
method: generated
---

# LSO Legato service order and inventory

LSO Legato sits **inside** one provider: business applications (BSS) on one side, the Service
Orchestration Functionality (SOF) on the other. It is the technical-layer sibling of the
Sonata/Cantata product layer, and it is derived from TM Forum TMF641 (Service Ordering) and TMF638
(Service Inventory).

## Steps

1. **Register for order events.** `registerListener` (POST `/hub`); confirm with
   `retrieveEventSubscription` (GET `/hub/{id}`). Events delivered:
   `serviceOrderCreateEvent`, `serviceOrderStateChangeEvent`,
   `serviceOrderItemStateChangeEvent`, `serviceOrderInformationRequiredEvent`.
2. **Place the service order.** `createServiceOrder` (POST `/serviceOrder`) with one
   `serviceOrderItem` per service action (add / modify / delete), each carrying the service
   specification and its characteristics.
3. **Track it.** `retrieveServiceOrder` (GET `/serviceOrder/{id}`) for a single order;
   `listServiceOrder` with `state` and the `.gt` / `.lt` date range filters plus `offset`/`limit`
   for sweeps.
4. **Answer information-required events** promptly — an order sitting in that state does not
   progress on its own.
5. **Reconcile against inventory.** After completion, `serviceFind` (GET `/service`) to search and
   `serviceGet` (GET `/service/{id}`) to read the delivered service. Subscribe to the Service
   Inventory notification API for `ServiceCreateEvent`, `serviceStateChangeEvent`,
   `serviceAttributeValueChangeEvent` and `serviceDeleteEvent` if you keep a local mirror.
6. **Tear down** with `unregisterListener` (DELETE `/hub/{id}`).

## Rules

- The Service Inventory API is **read-only** — `serviceFind` and `serviceGet` only. Inventory
  changes are a *consequence* of orders; never try to write inventory directly.
- The same operation set is published on LSO Interlude (inter-provider operational layer) and LSO
  Allegro (customer-facing operational layer). Choose by IRP, not by capability.
- `501 notImplemented` is a legitimate answer for optional operations; treat it as a capability
  signal and cache it, do not retry.
