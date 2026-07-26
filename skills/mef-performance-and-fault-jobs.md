---
name: LSO performance and fault management jobs
description: Set up SLA measurement and fault-data collection over MEF/Mplify LSO Allegro, Interlude or Legato — create a profile, run a monitoring job, suspend/resume/cancel it, and pull the resulting reports.
api: openapi/mef-lso-allegro-performance-monitoring-openapi.yml
apis:
  - openapi/mef-lso-allegro-performance-monitoring-openapi.yml
  - openapi/mef-lso-allegro-performance-notification-openapi.yml
  - openapi/mef-lso-allegro-fault-management-openapi.yml
  - openapi/mef-lso-allegro-streaming-management-openapi.yml
  - asyncapi/mef-lso-interlude-performance.template-asyncapi.yml
operations:
  - createPerformanceProfile
  - listPerformanceProfile
  - modifyPerformanceProfile
  - deletePerformanceProfile
  - createPerformanceJob
  - retrievePerformanceJob
  - suspendPerformanceJob
  - resumePerformanceJob
  - createCancelPerformanceJob
  - createModifyPerformanceJob
  - createPerformanceReport
  - retrievePerformanceReport
  - performanceReportComplexQuery
  - createFaultManagementJob
  - retrieveFaultManagementJob
  - suspendFaultManagementJob
  - resumeFaultManagementJob
  - listTrackingRecord
  - registerListener
generated: '2026-07-25'
method: generated
---

# LSO performance and fault management jobs

Service assurance at the operational layer. The **job** is the unit of work: you define what to
measure with a profile, run it as a job, and collect reports. Performance Monitoring (v5) and Fault
Management (v3) share the identical job shape, so one mental model covers both.

## Steps

1. **Define a profile** (performance only). `createPerformanceProfile` (POST
   `/performanceProfile`) fixes the granularity, the measurement set and the reporting period.
   `listPerformanceProfile`, `modifyPerformanceProfile` (PATCH) and `deletePerformanceProfile`
   maintain it. Reuse profiles — do not create one per job.
2. **Subscribe.** `registerListener` (POST `/hub`) for `performanceJobStateChangeEvent`,
   `performanceJobReportReadyEvent` and `performanceJobReportPreparationErrorEvent` (fault side:
   `faultManagementJobStateChangeEvent`, `faultManagementJobReportReadyEvent`).
   **Report-ready is an event, not a poll.**
3. **Start the job.** `createPerformanceJob` (POST `/performanceJob`) referencing the profile and
   the service(s) to measure; `createFaultManagementJob` for fault data.
4. **Control it in flight.** `suspendPerformanceJob` and `resumePerformanceJob` are POSTs to
   `/performanceJob/{id}/suspend|resume`. **Changing or cancelling a running job is itself a
   request object**: `createModifyPerformanceJob` and `createCancelPerformanceJob` create tracked
   requests the Seller may accept or reject — read back with
   `retrieveModifyPerformanceJob` / `retrieveCancelPerformanceJob`.
5. **Collect results.** `createPerformanceReport` for an on-demand report;
   `retrievePerformanceReport` to read one. For large result sets use
   `performanceReportComplexQuery` / `performanceJobComplexQuery` (POST) instead of long query
   strings — that is what they exist for.
6. **Audit.** `listTrackingRecord` returns the change history the Seller keeps for these jobs.
7. **Stream instead of poll** for continuous data: the Streaming Management API manages topics and
   subscriptions (`topicList`, `topicById`, `subscribeTopic`, `unsubscribeTopic`,
   `subscriptionList`, `subscriptionById`) and the payloads are described by the published
   AsyncAPI 2.0.0 performance template.

## Rules

- Complex-query POSTs still return the paginated headers (`X-Total-Count`, `X-Result-Count`,
  `X-Pagination-Throttled`) — honour them.
- Job state transitions are Seller-driven. Never assume a suspend took effect; wait for the state
  change event or re-read the job.
- The identical job APIs appear on Interlude and Legato with the same operationIds; only the IRP
  and base path differ.
