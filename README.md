# MEF (mef)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MEF — rebranded as Mplify Alliance on 24 June 2025 — is a US-headquartered nonprofit industry alliance of network, cloud, cybersecurity and enterprise organizations that defines the standards behind Carrier Ethernet, SD-WAN, SASE and Network-as-a-Service, and that publishes the LSO (Lifecycle Service Orchestration) API suite used by carriers to automate wholesale and inter-provider business and operational transactions. MEF sits on the wireline/standards side of the telecom value chain: it does not operate a network and sells no connectivity, it produces specifications, SDKs, an interop test service and the MEF 3.0 LSO API Certification Program that service providers and their software vendors implement. Its API posture is unusually open for this sector — the LSO Cantata, Sonata, Allegro, Interlude, Legato and Presto SDKs are published as Apache-2.0 OpenAPI documents in the public MEF-GIT GitHub organization, and lso.mplify.net is a genuine, no-login developer portal with an API catalog, payload catalog, an API blending tool and SDK release downloads. The membership wall sits one layer in, not around the specs: the per-API Developer Guides on GitHub and the test-requirements documents on the Mplify wiki are member-only, while the machine-readable API definitions themselves are free to anyone. On network APIs MEF is a GSMA Open Gateway MOU signatory (announced 11 November 2025, alongside the GSMA, the Linux Foundation and TM Forum) and ships a pre-standard LSO Quality on Demand payload schema explicitly aligned to the CAMARA QoD API — it complements CAMARA on the wireline side rather than exposing CAMARA endpoints itself, because it has no network to expose.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/mef/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/mef/refs/heads/main/apis.yml)

## Tags

- Telecommunications
- United States
- Standards
- LSO
- Network APIs
- CAMARA
- Open Gateway
- BSS
- OSS
- Carrier Ethernet
- SD-WAN
- SASE
- NaaS
- Service Orchestration
- Interconnection
- Certification

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## What Was Found

- **Developer portal:** [https://lso.mplify.net/](https://lso.mplify.net/) — HTTP 200, a real self-serve portal with no login wall. Also served at [https://lso.mef.net/](https://lso.mef.net/).
- **Machine-readable specs:** 94 OpenAPI documents and 1 AsyncAPI document harvested verbatim from the public, Apache-2.0 [MEF-GIT](https://github.com/MEF-GIT) GitHub organization at the current `kylie` release tag.
- **CAMARA posture:** standards-body partner, not an implementer. MEF signed the GSMA Open Gateway MOU on 11 November 2025 alongside the GSMA, the Linux Foundation and TM Forum, and ships a pre-standard LSO Quality on Demand payload schema modelled on the CAMARA QoD session object. MEF exposes no callable CAMARA endpoint — it has no network to expose.
- **TM Forum:** not a conformance-certification holder but a downstream consumer — the LSO specs carry explicit TMF633 / TMF638 / TMF641 attribution under the TM Forum's Apache 2.0 licence. MEF runs its own MEF 3.0 LSO API Certification Program instead.
- **Auth:** OAuth 2.0 client credentials (machine-to-machine), declared only in the `generated/security` variants of each SDK. **CIBA does not appear anywhere.** No OIDC discovery document is served.
- **Webhooks:** yes — TM Forum-style hub/listener callbacks; 39 of the 94 OpenAPI documents are notification definitions.
- **Client SDKs:** none. "SDK" here means a versioned zip of specification documents, not client libraries.
- **MCP:** each SDK ships a Python Model Context Protocol server (`mplify-mcp-runner`) generated over every Seller-side API — unusual for a standards body.
- **Where the wall is:** the OpenAPI is free; the per-API Developer Guide PDFs and the MEF W92.1 test requirements are member-only ([wiki.mplify.net](https://wiki.mplify.net/), [members.mplify.net](https://members.mplify.net/)).

## Interface Reference Points

| IRP | Between | Layer | Specs |
| --- | --- | --- | --- |
| LSO Cantata | Customer ↔ Service Provider | Business / product | 23 |
| LSO Sonata | Service Provider ↔ Service Provider | Business / product | 23 |
| LSO Allegro | Customer ↔ Service Provider | Operational / service | 14 |
| LSO Interlude | Service Provider ↔ Service Provider | Operational / service | 14 + 1 AsyncAPI |
| LSO Legato | Business Applications ↔ Service Orchestration Functionality | Intra-provider | 16 |
| LSO Presto | Service Orchestration Functionality ↔ Infrastructure Control & Management | MEF 60 NRP | 4 |

## Common Properties

- [Website](https://www.mplify.net/) — Website
- [DeveloperPortal](https://lso.mplify.net/) — DeveloperPortal
- [Documentation](https://lso.mplify.net/api-catalog) — Documentation
- [GitHubOrganization](https://github.com/MEF-GIT) — GitHubOrganization
- [SDK](https://lso.mplify.net/lso-api-sdk-releases) — SDK
- [LSO Tools](https://lso.mplify.net/lso-tools) — Tools
- [LSO API Blender](https://lso.mef.net/api-blender) — Tools
- [LSO Payload Catalog](https://lso.mplify.net/lso-payload-catalog) — Documentation
- [Network APIs](https://lso.mplify.net/network-apis) — Documentation
- [GettingStarted](https://lso.mplify.net/evaluate-lso-apis) — GettingStarted
- [GettingStarted](https://lso.mplify.net/implement-lso-apis) — GettingStarted
- [Support](https://lso.mplify.net/support) — Support
- [MEF 3.0 LSO API Certification Program](https://www.mplify.net/certification/testing-certifications-for-lso-apis/lso-api-certification/) — Certification
- [LSO API Onboarding & Interop Test (OIT) Service](https://www.mplify.net/certification/testing-certifications-for-lso-apis/lso-api-test-service/) — Testing
- [Partners](https://www.mplify.net/service-automation/lso-api-implementation/lso-partners-directory/) — Partners
- [MEF LSO APIs for Business Automation](https://www.mplify.net/lso/) — Overview
- [Mplify Wiki (member-gated content)](https://wiki.mplify.net/) — Wiki
- [Membership](https://www.mplify.net/join-mplify/) — Membership
- [Apache License 2.0](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/LICENSE) — License
- [LinkedIn](https://www.linkedin.com/company/mplifyalliance/) — LinkedIn
- [Bluesky](https://bsky.app/profile/mplifyalliance.bsky.social) — Bluesky

## APIs (95)

### LSO Sonata (23)

#### MEF LSO Sonata Product Offering Availability And Pricing Discovery Management

Product Offering Availability And Pricing Discovery Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productOfferingAvailabilityAndPricingDiscovery/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-offering-availability-and-pricing-discovery-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/availabilityAndPricingDiscovery/productOfferingAvailabilityAndPricingDiscovery.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/availabilityAndPricingDiscovery/productOfferingAvailabilityAndPricingDiscovery.api.yaml)

#### MEF LSO Sonata Billing Management

Billing Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 5 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/customerBillManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-billing-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/billing/billingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/billing/billingManagement.api.yaml)

#### MEF LSO Sonata Billing Notification

Billing Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/customerBillNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-billing-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/billing/billingNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/billing/billingNotification.api.yaml)

#### MEF LSO Sonata Product Catalog

Product Catalog — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 8 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `http://{serverBase}/mefApi/sonata/productCatalog/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-catalog-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/catalog/productCatalog.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/catalog/productCatalog.api.yaml)

#### MEF LSO Sonata Product Catalog Notification

Product Catalog Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 8 path(s), 8 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productCatalogNotifications/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-catalog-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/catalog/productCatalogNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/catalog/productCatalogNotification.api.yaml)

#### MEF LSO Sonata Circuit Impairment and Maintenance

Circuit Impairment and Maintenance — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/cimIncident/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-circuit-impairment-and-maintenance-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/cim/circuitImpairmentAndMaintenance.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/cim/circuitImpairmentAndMaintenance.api.yaml)

#### MEF LSO Sonata Circuit Impairment and Maintenance Notification

Circuit Impairment and Maintenance Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 3 path(s), 3 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/cimIncidentNotification/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-circuit-impairment-and-maintenance-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/cim/circuitImpairmentAndMaintenanceNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/cim/circuitImpairmentAndMaintenanceNotification.api.yaml)

#### MEF LSO Sonata Product Inventory Management

Product Inventory Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productInventory/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-inventory-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/inventory/productInventoryManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/inventory/productInventoryManagement.api.yaml)

#### MEF LSO Sonata Product Ordering Management

Product Ordering Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 10 path(s), 16 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productOrderingManagement/v11/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-order-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/order/productOrderManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/order/productOrderManagement.api.yaml)

#### MEF LSO Sonata Product Ordering Notification

Product Ordering Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 9 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productOrderingNotification/v11/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-order-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/order/productOrderNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/order/productOrderNotification.api.yaml)

#### MEF LSO Sonata Quote Management

Quote Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 6 path(s), 8 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/quoteManagement/v10/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-quote-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/quote/quoteManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/quote/quoteManagement.api.yaml)

#### MEF LSO Sonata Quote Notification

Quote Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/quoteNotification/v10/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-quote-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/quote/quoteNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/quote/quoteNotification.api.yaml)

#### MEF LSO Sonata Geographic Address Management

Geographic Address Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 5 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/geographicAddressManagement/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-geographic-address-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/serviceability/address/geographicAddressManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/serviceability/address/geographicAddressManagement.api.yaml)

#### MEF LSO Sonata Geographic Address Notification

Geographic Address Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 1 path(s), 1 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/geographicAddressNotification/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-geographic-address-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/serviceability/address/geographicAddressNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/serviceability/address/geographicAddressNotification.api.yaml)

#### MEF LSO Sonata Product Offering Qualification Management

Product Offering Qualification Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productOfferingQualification/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-offering-qualification-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationManagement.api.yaml)

#### MEF LSO Sonata Product Offering Qualification Notification

Product Offering Qualification Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/productOfferingQualificationNotification/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-product-offering-qualification-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationNotification.api.yaml)

#### MEF LSO Sonata Geographic Site Management

Geographic Site Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/geographicSiteManagement/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-geographic-site-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/serviceability/site/geographicSiteManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/serviceability/site/geographicSiteManagement.api.yaml)

#### MEF LSO Sonata Trouble Ticket and Incident Management

Trouble Ticket and Incident Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 9 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/troubleTicket/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-trouble-ticket-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/troubleTicket/troubleTicketManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/troubleTicket/troubleTicketManagement.api.yaml)

#### MEF LSO Sonata Trouble Ticket and Incident Notification

Trouble Ticket and Incident Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 7 path(s), 7 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/troubleTicketNotification/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-trouble-ticket-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/troubleTicket/troubleTicketNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/troubleTicket/troubleTicketNotification.api.yaml)

#### MEF LSO Sonata Appointment Management

Appointment Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 6 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/appointment/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-appointment-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/workforce/appointment/appointmentManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/workforce/appointment/appointmentManagement.api.yaml)

#### MEF LSO Sonata Appointment Management Notification

Appointment Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/appointmentNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-appointment-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/workforce/appointment/appointmentNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/workforce/appointment/appointmentNotification.api.yaml)

#### MEF LSO Sonata WorkOrder Management

WorkOrder Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/workOrderManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-workorder-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/workforce/workorder/workorderManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/workforce/workorder/workorderManagement.api.yaml)

#### MEF LSO Sonata WorkOrder Management Notification

WorkOrder Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Sonata SDK, Kylie release. LSO Sonata is the Interface Reference Point between two Service Providers (Buyer and Seller), covering inter-provider business/product automation. 3 path(s), 3 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/sonata/workOrderNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-sonata-workorder-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Sonata-SDK/kylie/productApi/workforce/workorder/workorderNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/productApi/workforce/workorder/workorderNotification.api.yaml)

### LSO Cantata (23)

#### MEF LSO Cantata Product Offering Availability And Pricing Discovery Management

Product Offering Availability And Pricing Discovery Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productOfferingAvailabilityAndPricingDiscovery/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-offering-availability-and-pricing-discovery-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/availabilityAndPricingDiscovery/productOfferingAvailabilityAndPricingDiscovery.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/availabilityAndPricingDiscovery/productOfferingAvailabilityAndPricingDiscovery.api.yaml)

#### MEF LSO Cantata Billing Management

Billing Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 5 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/customerBillManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-billing-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/billing/billingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/billing/billingManagement.api.yaml)

#### MEF LSO Cantata Billing Notification

Billing Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/customerBillNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-billing-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/billing/billingNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/billing/billingNotification.api.yaml)

#### MEF LSO Cantata Product Catalog

Product Catalog — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 8 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `http://{serverBase}/mefApi/cantata/productCatalog/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-catalog-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/catalog/productCatalog.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/catalog/productCatalog.api.yaml)

#### MEF LSO Cantata Product Catalog Notification

Product Catalog Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 8 path(s), 8 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productCatalogNotifications/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-catalog-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/catalog/productCatalogNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/catalog/productCatalogNotification.api.yaml)

#### MEF LSO Cantata Circuit Impairment and Maintenance

Circuit Impairment and Maintenance — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/cimIncident/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-circuit-impairment-and-maintenance-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/cim/circuitImpairmentAndMaintenance.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/cim/circuitImpairmentAndMaintenance.api.yaml)

#### MEF LSO Cantata Circuit Impairment and Maintenance Notification

Circuit Impairment and Maintenance Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 3 path(s), 3 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/cimIncidentNotification/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-circuit-impairment-and-maintenance-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/cim/circuitImpairmentAndMaintenanceNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/cim/circuitImpairmentAndMaintenanceNotification.api.yaml)

#### MEF LSO Cantata Product Inventory Management

Product Inventory Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productInventory/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-inventory-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/inventory/productInventoryManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/inventory/productInventoryManagement.api.yaml)

#### MEF LSO Cantata Product Ordering Management

Product Ordering Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 10 path(s), 16 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productOrderingManagement/v6/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-order-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/order/productOrderManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/order/productOrderManagement.api.yaml)

#### MEF LSO Cantata Product Ordering Notification

Product Ordering Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 9 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productOrderingNotification/v6/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-order-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/order/productOrderNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/order/productOrderNotification.api.yaml)

#### MEF LSO Cantata Quote Management

Quote Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 6 path(s), 8 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/quoteManagement/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-quote-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/quote/quoteManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/quote/quoteManagement.api.yaml)

#### MEF LSO Cantata Quote Notification

Quote Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/quoteNotification/v4/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-quote-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/quote/quoteNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/quote/quoteNotification.api.yaml)

#### MEF LSO Cantata Geographic Address Management

Geographic Address Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 5 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/geographicAddressManagement/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-geographic-address-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/serviceability/address/geographicAddressManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/serviceability/address/geographicAddressManagement.api.yaml)

#### MEF LSO Cantata Geographic Address Notification

Geographic Address Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 1 path(s), 1 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/geographicAddressNotification/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-geographic-address-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/serviceability/address/geographicAddressNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/serviceability/address/geographicAddressNotification.api.yaml)

#### MEF LSO Cantata Product Offering Qualification Management

Product Offering Qualification Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productOfferingQualification/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-offering-qualification-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationManagement.api.yaml)

#### MEF LSO Cantata Product Offering Qualification Notification

Product Offering Qualification Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/productOfferingQualificationNotification/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-product-offering-qualification-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/serviceability/offeringQualification/productOfferingQualificationNotification.api.yaml)

#### MEF LSO Cantata Geographic Site Management

Geographic Site Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/geographicSiteManagement/v8/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-geographic-site-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/serviceability/site/geographicSiteManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/serviceability/site/geographicSiteManagement.api.yaml)

#### MEF LSO Cantata Trouble Ticket and Incident Management

Trouble Ticket and Incident Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 9 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/troubleTicket/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-trouble-ticket-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/troubleTicket/troubleTicketManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/troubleTicket/troubleTicketManagement.api.yaml)

#### MEF LSO Cantata Trouble Ticket and Incident Notification

Trouble Ticket and Incident Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 7 path(s), 7 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/troubleTicketNotification/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-trouble-ticket-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/troubleTicket/troubleTicketNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/troubleTicket/troubleTicketNotification.api.yaml)

#### MEF LSO Cantata Appointment Management

Appointment Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 6 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/appointment/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-appointment-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/workforce/appointment/appointmentManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/workforce/appointment/appointmentManagement.api.yaml)

#### MEF LSO Cantata Appointment Management Notification

Appointment Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 2 path(s), 2 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/appointmentNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-appointment-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/workforce/appointment/appointmentNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/workforce/appointment/appointmentNotification.api.yaml)

#### MEF LSO Cantata WorkOrder Management

WorkOrder Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/workOrderManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-workorder-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/workforce/workorder/workorderManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/workforce/workorder/workorderManagement.api.yaml)

#### MEF LSO Cantata WorkOrder Management Notification

WorkOrder Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Cantata SDK, Kylie release. LSO Cantata is the Interface Reference Point between a Customer (typically an enterprise) and a Service Provider, covering the business/product layer. 3 path(s), 3 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/cantata/workOrderNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-cantata-workorder-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Cantata-SDK/kylie/productApi/workforce/workorder/workorderNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Cantata-SDK/blob/kylie/productApi/workforce/workorder/workorderNotification.api.yaml)

### LSO Interlude (15)

#### MEF LSO Interlude Alarm Management

Alarm Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/alarmManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-alarm-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/alarm/alarmManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/alarm/alarmManagement.api.yaml)

#### MEF LSO Interlude Alarm Notification

Alarm Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/alarmNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-alarm-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/alarm/alarmNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/alarm/alarmNotification.api.yaml)

#### MEF LSO Interlude Fault Management

Fault Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 15 path(s), 19 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/faultManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-fault-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/fm/faultManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/fm/faultManagement.api.yaml)

#### MEF LSO Interlude Fault Management Notification

Fault Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 9 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/faultNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-fault-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/fm/faultNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/fm/faultNotification.api.yaml)

#### MEF LSO Interlude Service Inventory Management

Service Inventory Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/serviceInventory/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-service-inventory-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/inventory/serviceInventoryManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/inventory/serviceInventoryManagement.api.yaml)

#### MEF LSO Interlude Service Inventory Notification

Service Inventory Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/serviceInventoryNotification/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-service-inventory-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/inventory/serviceInventoryNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/inventory/serviceInventoryNotification.api.yaml)

#### MEF LSO Interlude Service Ordering Management

Service Ordering Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/serviceOrderingManagement/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-service-ordering-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/order/serviceOrderingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/order/serviceOrderingManagement.api.yaml)

#### MEF LSO Interlude Service Ordering Notification

Service Ordering Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/serviceOrderingNotification/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-service-ordering-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/order/serviceOrderingNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/order/serviceOrderingNotification.api.yaml)

#### MEF LSO Interlude Performance Monitoring

Performance Monitoring — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 17 path(s), 25 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/performanceMonitoring/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-performance-monitoring-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/pm/performanceMonitoring.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/pm/performanceMonitoring.api.yaml)

#### MEF LSO Interlude Performance Monitoring Notification

Performance Monitoring Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 12 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/performanceNotification/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-performance-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/pm/performanceNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/pm/performanceNotification.api.yaml)

#### MEF LSO Interlude MEF 133.1 streaming template

MEF 133.1 streaming template — the AsyncAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 1 path(s), 0 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)

##### Properties

- [AsyncAPI](asyncapi/mef-lso-interlude-performance.template-asyncapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/pm/streaming/performance.template.asyncapi.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/pm/streaming/performance.template.asyncapi.yaml)

#### MEF LSO Interlude Streaming Management

Streaming Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/streamingManagement/v1`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-streaming-management-all-in-one-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/pm/streamingManagement.api.all-in-one.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/pm/streamingManagement.api.all-in-one.yaml)

#### MEF LSO Interlude Streaming Management

Streaming Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/streamingManagement/v1`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-streaming-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/pm/streamingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/pm/streamingManagement.api.yaml)

#### MEF LSO Interlude Service Function Testing

Service Function Testing — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 16 path(s), 25 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/serviceFunctionTesting/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-service-function-test-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/sft/serviceFunctionTest.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/sft/serviceFunctionTest.api.yaml)

#### MEF LSO Interlude Service Function Testing Notification

Service Function Testing Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Interlude SDK, Kylie release. LSO Interlude is the Interface Reference Point between two Service Providers, covering inter-provider operational/service automation. 12 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/interlude/serviceFunctionTestingNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-interlude-service-function-test-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Interlude-SDK/kylie/serviceApi/sft/serviceFunctionTestNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Interlude-SDK/blob/kylie/serviceApi/sft/serviceFunctionTestNotification.api.yaml)

### LSO Legato (16)

#### MEF LSO Legato Alarm Management

Alarm Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/alarmManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-alarm-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/alarm/alarmManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/alarm/alarmManagement.api.yaml)

#### MEF LSO Legato Alarm Notification

Alarm Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/alarmNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-alarm-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/alarm/alarmNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/alarm/alarmNotification.api.yaml)

#### MEF LSO Legato Legato Service Catalog API

Legato Service Catalog API — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{server}:{port}{basePath}`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-catalog-api-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/catalog/serviceCatalogApi.openapi.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/catalog/serviceCatalogApi.openapi.yaml)

#### MEF LSO Legato Legato Service Catalog Notification API

Legato Service Catalog Notification API — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 3 path(s), 3 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{server}:{port}{basePath}`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-catalog-notification-api-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/catalog/serviceCatalogNotificationApi.openapi.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/catalog/serviceCatalogNotificationApi.openapi.yaml)

#### MEF LSO Legato Fault Management

Fault Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 15 path(s), 19 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/faultManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-fault-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/fm/faultManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/fm/faultManagement.api.yaml)

#### MEF LSO Legato Fault Management Notification

Fault Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 9 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/faultNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-fault-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/fm/faultNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/fm/faultNotification.api.yaml)

#### MEF LSO Legato Service Inventory Management

Service Inventory Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/serviceInventory/v7/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-inventory-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/inventory/serviceInventoryManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/inventory/serviceInventoryManagement.api.yaml)

#### MEF LSO Legato Service Inventory Notification

Service Inventory Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/serviceInventoryNotification/v7/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-inventory-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/inventory/serviceInventoryNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/inventory/serviceInventoryNotification.api.yaml)

#### MEF LSO Legato Service Ordering Management

Service Ordering Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/serviceOrderingManagement/v6/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-ordering-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/order/serviceOrderingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/order/serviceOrderingManagement.api.yaml)

#### MEF LSO Legato Service Ordering Notification

Service Ordering Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/serviceOrderingNotification/v6/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-ordering-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/order/serviceOrderingNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/order/serviceOrderingNotification.api.yaml)

#### MEF LSO Legato Performance Monitoring

Performance Monitoring — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 17 path(s), 25 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/performanceMonitoring/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-performance-monitoring-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/pm/performanceMonitoring.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/pm/performanceMonitoring.api.yaml)

#### MEF LSO Legato Performance Monitoring Notification

Performance Monitoring Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 12 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/performanceNotification/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-performance-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/pm/performanceNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/pm/performanceNotification.api.yaml)

#### MEF LSO Legato Streaming Management

Streaming Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/streamingManagement/v1`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-streaming-management-all-in-one-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/pm/streamingManagement.api.all-in-one.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/pm/streamingManagement.api.all-in-one.yaml)

#### MEF LSO Legato Streaming Management

Streaming Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/streamingManagement/v1`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-streaming-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/pm/streamingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/pm/streamingManagement.api.yaml)

#### MEF LSO Legato Service Function Testing

Service Function Testing — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 16 path(s), 25 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/serviceFunctionTesting/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-function-test-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/sft/serviceFunctionTest.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/sft/serviceFunctionTest.api.yaml)

#### MEF LSO Legato Service Function Testing Notification

Service Function Testing Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Legato SDK, Kylie release. LSO Legato is the Interface Reference Point between Business Applications (BUS) and the Service Orchestration Functionality (SOF) inside a single Service Provider. 12 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/legato/serviceFunctionTestingNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-legato-service-function-test-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Legato-SDK/kylie/serviceApi/sft/serviceFunctionTestNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Legato-SDK/blob/kylie/serviceApi/sft/serviceFunctionTestNotification.api.yaml)

### LSO Allegro (14)

#### MEF LSO Allegro Alarm Management

Alarm Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/alarmManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-alarm-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/alarm/alarmManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/alarm/alarmManagement.api.yaml)

#### MEF LSO Allegro Alarm Notification

Alarm Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/alarmNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-alarm-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/alarm/alarmNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/alarm/alarmNotification.api.yaml)

#### MEF LSO Allegro Fault Management

Fault Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 15 path(s), 19 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/faultManagement/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-fault-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/fm/faultManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/fm/faultManagement.api.yaml)

#### MEF LSO Allegro Fault Management Notification

Fault Management Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 9 path(s), 9 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/faultNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-fault-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/fm/faultNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/fm/faultNotification.api.yaml)

#### MEF LSO Allegro Service Inventory Management

Service Inventory Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 5 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/serviceInventory/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-service-inventory-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/inventory/serviceInventoryManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/inventory/serviceInventoryManagement.api.yaml)

#### MEF LSO Allegro Service Inventory Notification

Service Inventory Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/serviceInventoryNotification/v2/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-service-inventory-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/inventory/serviceInventoryNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/inventory/serviceInventoryNotification.api.yaml)

#### MEF LSO Allegro Service Ordering Management

Service Ordering Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/serviceOrderingManagement/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-service-ordering-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/order/serviceOrderingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/order/serviceOrderingManagement.api.yaml)

#### MEF LSO Allegro Service Ordering Notification

Service Ordering Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 4 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/serviceOrderingNotification/v1/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-service-ordering-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/order/serviceOrderingNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/order/serviceOrderingNotification.api.yaml)

#### MEF LSO Allegro Performance Monitoring

Performance Monitoring — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 17 path(s), 25 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/performanceMonitoring/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-performance-monitoring-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/pm/performanceMonitoring.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/pm/performanceMonitoring.api.yaml)

#### MEF LSO Allegro Performance Monitoring Notification

Performance Monitoring Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 12 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/performanceNotification/v5/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-performance-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/pm/performanceNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/pm/performanceNotification.api.yaml)

#### MEF LSO Allegro Streaming Management

Streaming Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/streamingManagement/v1`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-streaming-management-all-in-one-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/pm/streamingManagement.api.all-in-one.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/pm/streamingManagement.api.all-in-one.yaml)

#### MEF LSO Allegro Streaming Management

Streaming Management — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 4 path(s), 6 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/streamingManagement/v1`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-streaming-management-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/pm/streamingManagement.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/pm/streamingManagement.api.yaml)

#### MEF LSO Allegro Service Function Testing

Service Function Testing — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 16 path(s), 25 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/serviceFunctionTesting/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-service-function-test-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/sft/serviceFunctionTest.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/sft/serviceFunctionTest.api.yaml)

#### MEF LSO Allegro Service Function Testing Notification

Service Function Testing Notification — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Allegro SDK, Kylie release. LSO Allegro is the Interface Reference Point between a Customer and a Service Provider, covering the operational/service layer. 12 path(s), 12 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/tree/kylie)
- **Base URL:** `https://{serverBase}/mefApi/allegro/serviceFunctionTestingNotification/v3/`

##### Properties

- [OpenAPI](openapi/mef-lso-allegro-service-function-test-notification-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Allegro-SDK/kylie/serviceApi/sft/serviceFunctionTestNotification.api.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Allegro-SDK/blob/kylie/serviceApi/sft/serviceFunctionTestNotification.api.yaml)

### LSO Presto (4)

#### MEF LSO Presto mef-common,tapi-topology,tapi-common,tapi-connectivity,mef-common-types,nrm-connectivity,nrp-interface API

mef-common,tapi-topology,tapi-common,tapi-connectivity,mef-common-types,nrm-connectivity,nrp-interface API — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Presto SDK, Kylie release. LSO Presto is the Interface Reference Point between the Service Orchestration Functionality (SOF) and the Infrastructure Control and Management (ICM) layer, defined by MEF 60 Network Resource Provisioning. 17 path(s), 17 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie)

##### Properties

- [OpenAPI](openapi/mef-lso-presto-nrp-rcp-only-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Presto-SDK/kylie/api/swagger/additions/presto-nrp-rcp-only.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/blob/kylie/api/swagger/additions/presto-nrp-rcp-only.yaml)

#### MEF LSO Presto mef-common,tapi-topology,tapi-common,tapi-connectivity,mef-common-types,nrm-connectivity,nrp-interface API

mef-common,tapi-topology,tapi-common,tapi-connectivity,mef-common-types,nrm-connectivity,nrp-interface API — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Presto SDK, Kylie release. LSO Presto is the Interface Reference Point between the Service Orchestration Functionality (SOF) and the Infrastructure Control and Management (ICM) layer, defined by MEF 60 Network Resource Provisioning. 14 path(s), 14 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie)

##### Properties

- [OpenAPI](openapi/mef-lso-presto-nrp-rpc-only-simplified-hierarchy-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Presto-SDK/kylie/api/swagger/additions/presto-nrp-rpc-only-simplified-hierarchy.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/blob/kylie/api/swagger/additions/presto-nrp-rpc-only-simplified-hierarchy.yaml)

#### MEF LSO Presto mef-common,tapi-topology,tapi-common,tapi-connectivity,mef-common-types,nrm-connectivity,nrp-interface API

mef-common,tapi-topology,tapi-common,tapi-connectivity,mef-common-types,nrm-connectivity,nrp-interface API — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Presto SDK, Kylie release. LSO Presto is the Interface Reference Point between the Service Orchestration Functionality (SOF) and the Infrastructure Control and Management (ICM) layer, defined by MEF 60 Network Resource Provisioning. 32 path(s), 32 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie)

##### Properties

- [OpenAPI](openapi/mef-lso-presto-nrp-simplified-hierarchy-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Presto-SDK/kylie/api/swagger/additions/presto-nrp-simplified-hierarchy.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/blob/kylie/api/swagger/additions/presto-nrp-simplified-hierarchy.yaml)

#### MEF LSO Presto Network Resource Provisioning

Network Resource Provisioning — the OpenAPI definition published by Mplify (formerly MEF) in the MEF LSO Presto SDK, Kylie release. LSO Presto is the Interface Reference Point between the Service Orchestration Functionality (SOF) and the Infrastructure Control and Management (ICM) layer, defined by MEF 60 Network Resource Provisioning. 32 path(s), 32 operation(s). Apache-2.0 licensed and openly downloadable from public GitHub.

- **Human URL:** [https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/tree/kylie)

##### Properties

- [OpenAPI](openapi/mef-lso-presto-nrp-openapi.yml)
- [Documentation](https://lso.mplify.net/api-catalog)
- [APIReference](https://raw.githubusercontent.com/MEF-GIT/MEF-LSO-Presto-SDK/kylie/api/swagger/presto-nrp.yaml)
- [SourceCode](https://github.com/MEF-GIT/MEF-LSO-Presto-SDK/blob/kylie/api/swagger/presto-nrp.yaml)

## Maintainers

- Kin Lane — kin@apievangelist.com
