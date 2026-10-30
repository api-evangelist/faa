# Federal Aviation Administration

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

The Federal Aviation Administration (FAA) is the United States civil aviation authority, an operating administration of the U.S. Department of Transportation. It regulates and certificates aircraft, airmen, airports and air carriers, operates the National Airspace System and its air traffic control, and issues the aeronautical information the entire U.S. travel and aviation chain runs on — NOTAMs, TFRs, charts, the 28-day NASR subscription, aircraft registration and airport data. It sits upstream of commercial travel distribution rather than inside it — the FAA sells no inventory and is not a GDS, NDC or channel participant, but every airline, GDS, OTA, flight-planning app and drone service supplier in the United States consumes FAA data as a source of truth. Its API posture is genuinely mixed and honest reporting requires saying so. The Airport Status Web Service and the Aeronautic Product Release API are published under a Creative Commons Zero licence, answer unauthenticated over HTTPS, and ship real OpenAPI 3.0.1 documents through a public Gravitee developer portal at api.faa.gov. Alongside them the FAA runs a CKAN 2.11.4 catalog and two ArcGIS Open Data hubs with DCAT-US 1.1 feeds and bulk CSV/GeoJSON/KML export. But the NOTAM API, the Air Carrier Pilot Records Database API and SWIM are gated — client_id/client_secret headers, operator eligibility restricted by regulation, or an executed SWIM agreement — and LAANC drone authorization is reachable only through FAA-approved UAS Service Suppliers, never directly.

**Areas:** Travel · United States · Aviation · Airports · Government · Regulator · Open Data · Airspace · Drones · Aeronautical Information

## Federal Aviation Administration on APIs.io

Everything profiled for Federal Aviation Administration is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/faa/](https://apis.io/providers/faa/)** — or go straight to one of the APIs or properties below.

### APIs (35)

- [FAA NOTAM API](https://apis.io/apis/faa/faa-notam-api/) — Notices to Air Missions retrieval API. Probe-confirmed live but gated — an unauthenticated GET returned HTTP 401 with the body {"message":"Unauthorized",…
- [FAA NOTAM Management Service (NMS) API](https://apis.io/apis/faa/faa-nms-api/) — The distribution interface of the FAA's new NOTAM Management Service, the vendor-provided replacement for the legacy United States NOTAM System (USNS) and…
- [FAA NMS North Atlantic Track NOTAM Feed](https://apis.io/apis/faa/faa-nms-nat-track-feed/) — Unauthenticated JSON feed of North Atlantic Track NOTAMs published by the FAA NOTAM Management Service. Each record carries accountability and origin ids,…
- [FAA NMS System Metrics Feed](https://apis.io/apis/faa/faa-nms-metrics-feed/) — Unauthenticated JSON feed backing the NOTAM Management Service system metrics dashboard — cumulative NOTAMs processed, NMS API onboarded users, NMS API…
- [FAA DMS Lookup API](https://apis.io/apis/faa/faa-dms-lookup-api/) — Retrieves designee information from the FAA Data Management System using either a Designee Number or an ODA Key ID. Listed in the api.faa.gov portal under…
- [FAA Data Catalog API (CKAN)](https://apis.io/apis/faa/faa-data-catalog-ckan-api/) — The FAA's public data clearinghouse at catalog.data.faa.gov runs CKAN 2.11.4 and exposes the standard CKAN Action API. Verified 2026-07-28 — status_show…
- [FAA Aeronautical Information Services Open Data](https://apis.io/apis/faa/faa-ais-open-data/) — ArcGIS Open Data hub published by "Federal Aviation Administration - AIS" carrying 73 datasets — class airspace, frequencies, runways, navaids, obstacles,…
- [FAA UAS Data Delivery System Open Data](https://apis.io/apis/faa/faa-uas-data-delivery-system/) — ArcGIS Open Data hub for unmanned aircraft data — UAS Facility Maps (the LAANC altitude grid), national security UAS flight restrictions, part-time…
- [FAA NAS Status Airport Status Information Feed](https://apis.io/apis/faa/faa-nas-status-feed/) — Unauthenticated XML feed of national airspace system status — ground stop programs, ground delay programs, airport closures and arrival/departure delays —…
- [FAA Temporary Flight Restriction (TFR) List API](https://apis.io/apis/faa/faa-tfr-api/) — Unauthenticated JSON list of active Temporary Flight Restrictions, each carrying a NOTAM id, TFR type, ARTCC facility identifier, state and effective…
- [Federal Aviation Administration Air Carrier API](https://apis.io/apis/faa/faa-aircarrierapi-api/) — The AirCarrierApi API from Federal Aviation Administration — 4 operation(s) for aircarrierapi.
- [Federal Aviation Administration Axhsubmitdiscrepancies API](https://apis.io/apis/faa/faa-axhsubmitdiscrepancies-api/) — The Axhsubmitdiscrepancies API from Federal Aviation Administration — 1 operation(s) for axhsubmitdiscrepancies.
- [Federal Aviation Administration Coded Instrument Flight Procedures (CIFP) API](https://apis.io/apis/faa/faa-coded-instrument-flight-procedures-cifp-api/) — The Coded Instrument Flight Procedures (CIFP) API from Federal Aviation Administration — 2 operation(s) for coded instrument flight procedures (cifp).
- [Federal Aviation Administration Daily Digital Obstacle File (DDOF) API](https://apis.io/apis/faa/faa-daily-digital-obstacle-file-ddof-api/) — The Daily Digital Obstacle File (DDOF) API from Federal Aviation Administration — 2 operation(s) for daily digital obstacle file (ddof).
- [Federal Aviation Administration Digital Enroute Charts US (DDECUS) API](https://apis.io/apis/faa/faa-digital-enroute-charts-us-ddecus-api/) — The Digital Enroute Charts US (DDECUS) API from Federal Aviation Administration — 2 operation(s) for digital enroute charts us (ddecus).
- [Federal Aviation Administration Digital Enroute Supplement (DERS) API](https://apis.io/apis/faa/faa-digital-enroute-supplement-ders-api/) — The Digital Enroute Supplement (DERS) API from Federal Aviation Administration — 2 operation(s) for digital enroute supplement (ders).
- [Federal Aviation Administration FAA Airport Status Service API](https://apis.io/apis/faa/faa-faa-airport-status-service-api/) — The FAA Airport Status Service API from Federal Aviation Administration — 2 operation(s) for faa airport status service.
- [Federal Aviation Administration Grand Canyon VFR Chart API](https://apis.io/apis/faa/faa-grand-canyon-vfr-chart-api/) — The Grand Canyon VFR Chart API from Federal Aviation Administration — 2 operation(s) for grand canyon vfr chart.
- [Federal Aviation Administration Gulf of Mexico IFR Enroute Chart API](https://apis.io/apis/faa/faa-gulf-of-mexico-ifr-enroute-chart-api/) — The Gulf of Mexico IFR Enroute Chart API from Federal Aviation Administration — 2 operation(s) for gulf of mexico ifr enroute chart.
- [Federal Aviation Administration IFR Enroute Charts API](https://apis.io/apis/faa/faa-ifr-enroute-charts-api/) — The IFR Enroute Charts API from Federal Aviation Administration — 2 operation(s) for ifr enroute charts.
- [Federal Aviation Administration IFR Planning Charts API](https://apis.io/apis/faa/faa-ifr-planning-charts-api/) — The IFR Planning Charts API from Federal Aviation Administration — 2 operation(s) for ifr planning charts.
- [Federal Aviation Administration NASR 28 Day Subscription API](https://apis.io/apis/faa/faa-nasr-28-day-subscription-api/) — The NASR 28 Day Subscription API from Federal Aviation Administration — 2 operation(s) for nasr 28 day subscription.
- [Federal Aviation Administration Oceanic Route Charts API](https://apis.io/apis/faa/faa-oceanic-route-charts-api/) — The Oceanic Route Charts API from Federal Aviation Administration — 2 operation(s) for oceanic route charts.
- [Federal Aviation Administration Sectional Charts API](https://apis.io/apis/faa/faa-sectional-charts-api/) — The Sectional Charts API from Federal Aviation Administration — 2 operation(s) for sectional charts.
- [Federal Aviation Administration Supplement Chart API](https://apis.io/apis/faa/faa-supplement-chart-api/) — The Supplement Chart API from Federal Aviation Administration — 2 operation(s) for supplement chart .
- [Federal Aviation Administration Terminal Area Charts API](https://apis.io/apis/faa/faa-terminal-area-charts-api/) — The Terminal Area Charts API from Federal Aviation Administration — 2 operation(s) for terminal area charts.
- [Federal Aviation Administration US Terminal Procedures Publication (TPP) API](https://apis.io/apis/faa/faa-us-terminal-procedures-publication-tpp-api/) — The US Terminal Procedures Publication (TPP) API from Federal Aviation Administration — 2 operation(s) for us terminal procedures publication (tpp).
- [Federal Aviation Administration US VFR Wall Planning Chart API](https://apis.io/apis/faa/faa-us-vfr-wall-planning-chart-api/) — The US VFR Wall Planning Chart API from Federal Aviation Administration — 2 operation(s) for us vfr wall planning chart.
- [Federal Aviation Administration VFR Helicopter Route Chart API](https://apis.io/apis/faa/faa-vfr-helicopter-route-chart-api/) — The VFR Helicopter Route Chart API from Federal Aviation Administration — 4 operation(s) for vfr helicopter route chart.
- [FAA NOTAM](https://apis.io/apis/faa/notam-api/) — The FAA NOTAM API provides access to Notices to Air Missions (NOTAMs), which are time-critical aeronautical information that could affect a pilot's decision…
- [FAA Airport Status](https://apis.io/apis/faa/airport-status/) — The FAA Airport Status Web Service (ASWS) provides current airport conditions, including delays and ground stops, for major United States airports.…
- [FAA NASR Subscription](https://apis.io/apis/faa/nasr-subscription/) — The FAA National Airspace System Resources (NASR) Subscription provides authoritative aeronautical data covering airports, navigation aids, airways, fixes,…
- [FAA Airmen Registry](https://apis.io/apis/faa/airmen-registry/) — The FAA Airmen Registry provides downloadable data on certificated pilots and other airmen in the United States, including pilot certificates, ratings, and…
- [FAA Aircraft Registry](https://apis.io/apis/faa/aircraft-registry/) — The FAA Aircraft Registry provides downloadable data on civil aircraft registered in the United States, including registration, ownership, and airworthiness…
- [FAA System Wide Information Management](https://apis.io/apis/faa/swim/) — The FAA System Wide Information Management (SWIM) program is a service-oriented information sharing platform that delivers real-time National Airspace…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Faa Swim Event Surface](https://apis.io/asyncapis/faa/faa-swim-event-surface/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [faa](https://apis.io/servers/faa/faa/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Faa Agentic Access](https://apis.io/agentic-access/faa/faa-agentic-access/)

#### Collections (4)

Postman and Open Collection request collections.

- [Aeronautic Product Release API](https://apis.io/collections/faa/open-faa-aeronautic-product-release-api/)
- [PRD Air Carrier API](https://apis.io/collections/faa/open-faa-air-carrier-prd-api/)
- [Airport Status Web Service](https://apis.io/collections/faa/open-faa-airport-status-web-service/)
- [sas-api](https://apis.io/collections/faa/open-faa-safety-assurance-system-api/)

#### Overlays (4)

OpenAPI overlays, including conversational phrasing for each operation.

- [Faa Aeronautic Product Release Api Overlay](https://apis.io/overlays/faa/faa-aeronautic-product-release-api-overlay/)
- [Faa Air Carrier Prd Api Overlay](https://apis.io/overlays/faa/faa-air-carrier-prd-api-overlay/)
- [Faa Airport Status Web Service Overlay](https://apis.io/overlays/faa/faa-airport-status-web-service-overlay/)
- [Faa Safety Assurance System Api Overlay](https://apis.io/overlays/faa/faa-safety-assurance-system-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Faa Authentication](https://apis.io/security/faa/faa-authentication/)
- [Faa Domain Security](https://apis.io/security/faa/faa-domain-security/)
- [Faa Vulnerability Disclosure](https://apis.io/security/faa/faa-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Faa Plans](https://apis.io/plans/faa/faa-plans/)

#### Rate limits (1)

Published request limits.

- [Faa Rate Limits](https://apis.io/rate-limits/faa/faa-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.faa.gov/)
- [Documentation](https://api.faa.gov/)
- [Getting started](https://www.faa.gov/data)
- [API reference](https://api.faa.gov/)
- [Pricing](https://apim-api.apic4e.faa.gov/portal/environments/DEFAULT/apis/{id}/plans)
- [Sign up](https://portal.apic4e.faa.gov/)
- [Support](https://www.faa.gov/contact)
- [Blog](https://www.faa.gov/blog/cleared_for_takeoff)
- [Security](https://www.faa.gov/web_policies/vulnerability_disclosure_policy)
- [Terms of service](https://www.faa.gov/web_policies)
- [Privacy policy](https://www.faa.gov/privacy/)
- [GitHub](https://github.com/faa-swim)
- [Status](https://nms.aim.faa.gov/#system-metrics)

## API Evangelist rating

**Kin Score 53.5** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 48.1 |
| Contract governance | 4.5 |
| Operational transparency | 60.5 |
| Developer ergonomics | 56.5 |
| Access clarity | 63.2 |

**Agent readiness 28.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 30.4** — Government & Public Sector

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/faa/](https://apis.io/providers/faa/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Federal Aviation Administration: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/faa/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
