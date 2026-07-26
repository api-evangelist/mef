---
name: LSO trouble ticket lifecycle
description: Raise, track, update, close and reopen a trouble ticket against a delivered product over MEF/Mplify LSO Sonata or Cantata, and correlate it with Seller-declared incidents.
api: openapi/mef-lso-sonata-trouble-ticket-management-openapi.yml
apis:
  - openapi/mef-lso-sonata-trouble-ticket-management-openapi.yml
  - openapi/mef-lso-sonata-trouble-ticket-notification-openapi.yml
  - openapi/mef-lso-cantata-trouble-ticket-management-openapi.yml
operations:
  - createTroubleTicket
  - listTroubleTicket
  - retrieveTroubleTicket
  - patchTroubleTicket
  - cancelTroubleTicket
  - closeTroubleTicket
  - reopenTroubleTicket
  - listIncident
  - retrieveIncident
  - registerListener
  - unregisterListener
generated: '2026-07-25'
method: generated
---

# LSO trouble ticket lifecycle

Service assurance over the business layer. Same operation set in **Sonata** (Service Provider to
Service Provider) and **Cantata** (customer to Service Provider) — pick the IRP that matches who
you are.

## Steps

1. **Subscribe first.** `registerListener` (POST `/hub`) with your callback URL, before you open
   anything. The Seller then pushes `listenToTroubleTicketStatusChangeEvent`,
   `listenToTroubleTicketAttributeValueChangeEvent`,
   `listenToTroubleTicketInformationRequiredEvent` and `listenToTroubleTicketResolvedEvent`.
   Polling `retrieveTroubleTicket` is the fallback, not the design.
2. **Check for a known incident.** `listIncident` / `retrieveIncident` — if the Seller has already
   declared an incident covering the affected product, reference it instead of opening a duplicate.
3. **Open the ticket.** `createTroubleTicket` (POST `/troubleTicket`), referencing the affected
   product id from Product Inventory, with severity and a clear `description`.
4. **Answer information requests.** On `listenToTroubleTicketInformationRequiredEvent`, respond with
   `patchTroubleTicket` (PATCH `/troubleTicket/{id}`). A ticket stalled awaiting information is the
   single most common cause of missed resolution targets.
5. **Track.** `listTroubleTicket` filtered by `state` and the `creationDate.gt` / `creationDate.lt`
   range parameters; always with `buyerId` and `sellerId`.
6. **Terminate correctly.** Three distinct transitions, three distinct operations:
   `cancelTroubleTicket` (withdraw before work starts), `closeTroubleTicket` (accept the
   resolution), `reopenTroubleTicket` (the fix did not hold). They are POSTs to
   `/troubleTicket/{id}/cancel|close|reopen` — not PATCHes on a status field.
7. **Unsubscribe** when the integration is torn down: `unregisterListener` (DELETE `/hub/{id}`).

## Rules

- `403 forbiddenRequester` on a ticket you did not open is expected — Buyer scoping is enforced
  per party.
- `422 invalidValue` on severity or on a state transition means the Seller's state machine does not
  allow it from the current state; re-read the ticket before retrying.
- No idempotency key exists. Before re-issuing `createTroubleTicket` after a timeout, search
  `listTroubleTicket` by your `externalId`.
