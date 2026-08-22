# Federal Aviation Administration (faa)

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

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/faa/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/faa/refs/heads/main/apis.yml)

## Tags

- Travel
- United States
- Aviation
- Airports
- Government
- Regulator
- Open Data
- Airspace
- Drones
- Aeronautical Information

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

### FAA Airport Status Web Service (ASWS)

Airport delay summaries and per-airport status for 40+ major US national airports, sourced from fly.faa.gov and served as JSON or XML. Keyed on IATA three-letter airport codes. Answers unauthenticated and the OpenAPI declares a Creative Commons Zero (CC0) licence. Verified live 2026-07-28 (HTTP 200, real delay payload).

- **Human URL:** [https://api.faa.gov/](https://api.faa.gov/)
- **Base URL:** `https://external-api.faa.gov/asws/api`

#### Tags

- Airports
- Delays
- Flight Information
- Travel
- Open Data

#### Properties

- [OpenAPI](openapi/faa-airport-status-web-service-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.faa.gov/)
- [Website](https://nasstatus.faa.gov/)

### FAA Aeronautic Product Release API (APRA)

Chart publication metadata and download API from FAA Aeronautical Information Services. Thirty-four operations across VFR sectionals, terminal area charts, IFR enroute and oceanic charts, terminal procedures (dTPP), digital obstacle files, chart supplements, CIFP and the NFDC NASR 28-day subscription — each exposed as an /info edition lookup and a /chart download. Answers unauthenticated; responses use the FAA-proprietary arpa_response XML namespace. Verified live 2026-07-28 (HTTP 200).

- **Human URL:** [https://api.faa.gov/](https://api.faa.gov/)
- **Base URL:** `https://external-api.faa.gov/apra`

#### Tags

- Aeronautical Charts
- Aviation
- NASR
- Open Data
- Airports

#### Properties

- [OpenAPI](openapi/faa-aeronautic-product-release-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.faa.gov/)
- [Website](https://www.faa.gov/air_traffic/flight_info/aeronav)

### FAA Air Carrier PRD API

Machine interface for submitting and searching pilot records in the FAA Pilot Records Database, the reporting obligation created for air carriers by 14 CFR Part 111. Requires client_id and client_secret request headers. The FAA's own portal listing states access is restricted to operators under Part 121, 135, 125, 91K, Air Tour, Public Aircraft or 91 Corporate and that other public or private entities will not be authorized.

- **Human URL:** [https://api.faa.gov/](https://api.faa.gov/)
- **Base URL:** `https://external.apic4e.faa.gov`

#### Tags

- Pilot Records
- Airlines
- Compliance
- Aviation Safety
- Regulator

#### Properties

- [OpenAPI](openapi/faa-air-carrier-prd-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.faa.gov/)
- [Website](https://www.faa.gov/regulations_policies/pilot_records_database/)

### FAA Safety Assurance System (SAS) API

Single-operation API for submitting passenger discrepancy reports into the FAA Safety Assurance System. The harvested OpenAPI declares apiKey and appId header security schemes and carries a relative server URL; the portal lists external and internal Gravitee entrypoints.

- **Human URL:** [https://api.faa.gov/](https://api.faa.gov/)
- **Base URL:** `https://external.apic4e.faa.gov/axh-sasp-api/sas`

#### Tags

- Aviation Safety
- Compliance
- Reporting
- Regulator

#### Properties

- [OpenAPI](openapi/faa-safety-assurance-system-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.faa.gov/)

### FAA NOTAM API

Notices to Air Missions retrieval API. Probe-confirmed live but gated — an unauthenticated GET returned HTTP 401 with the body {"message":"Unauthorized", "http_status_code":401} on 2026-07-28, while the bare external-api.faa.gov host returns 404, so the route exists behind credentials. Access is via a client_id and client_secret issued from the api.faa.gov developer portal. No public OpenAPI was published for this API in the portal's public catalog, so none was harvested.

- **Human URL:** [https://api.faa.gov/](https://api.faa.gov/)
- **Base URL:** `https://external-api.faa.gov/notamapi/v1`

#### Tags

- NOTAM
- Flight Information
- Airspace
- Aviation

#### Properties

- [Documentation](https://api.faa.gov/)
- [Website](https://notams.aim.faa.gov/notamSearch/)

### FAA DMS Lookup API

Retrieves designee information from the FAA Data Management System using either a Designee Number or an ODA Key ID. Listed in the api.faa.gov portal under the "Public" category, but the only entrypoint the portal publishes is internal.apic4e.faa.gov, so no externally reachable base URL is documented and no OpenAPI page is attached.

- **Human URL:** [https://api.faa.gov/](https://api.faa.gov/)

#### Tags

- Designees
- Regulator
- Aviation

#### Properties

- [Documentation](https://api.faa.gov/)

### FAA Data Catalog API (CKAN)

The FAA's public data clearinghouse at catalog.data.faa.gov runs CKAN 2.11.4 and exposes the standard CKAN Action API. Verified 2026-07-28 — status_show returned site_title "Federal Aviation Administration" and ckan_version 2.11.4, and package_list returned six aeronautical chart product datasets. A DCAT-US 1.1 /data.json feed is also published.

- **Human URL:** [https://catalog.data.faa.gov/dataset](https://catalog.data.faa.gov/dataset)
- **Base URL:** `https://catalog.data.faa.gov/api/3/action`

#### Tags

- Open Data
- Data Catalog
- CKAN
- Aeronautical Charts

#### Properties

- [Documentation](https://catalog.data.faa.gov/dataset)
- [DCAT-US 1.1](https://catalog.data.faa.gov/data.json) — [DCAT-US 1.1 Specification](https://resources.data.gov/resources/dcat-us/)
- [Website](https://www.faa.gov/data)

### FAA Aeronautical Information Services Open Data

ArcGIS Open Data hub published by "Federal Aviation Administration - AIS" carrying 73 datasets — class airspace, frequencies, runways, navaids, obstacles, VFR and IFR chart tile services. Every feature dataset is offered as an ArcGIS GeoServices REST FeatureServer plus bulk CSV, GeoJSON, KML and shapefile download, and the hub publishes a DCAT-US 1.1 catalog. Verified 2026-07-28 (HTTP 200, 73 datasets).

- **Human URL:** [https://ais-faa.opendata.arcgis.com/](https://ais-faa.opendata.arcgis.com/)
- **Base URL:** `https://services6.arcgis.com/ssFJjBXIUyZDrSYZ/arcgis/rest/services`

#### Tags

- Open Data
- Airspace
- GIS
- Airports
- Aeronautical Information

#### Properties

- [Documentation](https://ais-faa.opendata.arcgis.com/)
- [DCAT-US 1.1](https://ais-faa.opendata.arcgis.com/data.json) — [DCAT-US 1.1 Specification](https://resources.data.gov/resources/dcat-us/)

### FAA UAS Data Delivery System Open Data

ArcGIS Open Data hub for unmanned aircraft data — UAS Facility Maps (the LAANC altitude grid), national security UAS flight restrictions, part-time restrictions, FAA-Recognized Identification Areas and the Sporting Event Automated Monitoring System. 28 datasets, ArcGIS GeoServices REST plus CSV/GeoJSON/KML/ZIP export, DCAT-US 1.1 feed. Verified 2026-07-28 (HTTP 200, 28 datasets).

- **Human URL:** [https://udds-faa.opendata.arcgis.com/](https://udds-faa.opendata.arcgis.com/)
- **Base URL:** `https://services6.arcgis.com/ssFJjBXIUyZDrSYZ/arcgis/rest/services`

#### Tags

- Drones
- UAS
- Open Data
- Airspace
- GIS

#### Properties

- [Documentation](https://udds-faa.opendata.arcgis.com/)
- [DCAT-US 1.1](https://udds-faa.opendata.arcgis.com/api/feed/dcat-us/1.1.json) — [DCAT-US 1.1 Specification](https://resources.data.gov/resources/dcat-us/)

### FAA NAS Status Airport Status Information Feed

Unauthenticated XML feed of national airspace system status — ground stop programs, ground delay programs, airport closures and arrival/departure delays — as consumed by nasstatus.faa.gov. Verified live 2026-07-28 (HTTP 200, real ground stop and ground delay program data keyed on IATA airport codes).

- **Human URL:** [https://nasstatus.faa.gov/](https://nasstatus.faa.gov/)
- **Base URL:** `https://nasstatus.faa.gov/api/airport-status-information`

#### Tags

- Delays
- Airports
- Flight Information
- Travel
- Open Data

#### Properties

- [Website](https://nasstatus.faa.gov/)

### FAA Temporary Flight Restriction (TFR) List API

Unauthenticated JSON list of active Temporary Flight Restrictions, each carrying a NOTAM id, TFR type, ARTCC facility identifier, state and effective description. Verified live 2026-07-28 (HTTP 200, application/json, 28,701 bytes).

- **Human URL:** [https://tfr.faa.gov/](https://tfr.faa.gov/)
- **Base URL:** `https://tfr.faa.gov/tfrapi/exportTfrList`

#### Tags

- TFR
- Airspace
- NOTAM
- Open Data
- Aviation

#### Properties

- [Website](https://tfr.faa.gov/)

## Common Properties

- [Website](https://www.faa.gov/)
- [Documentation](https://api.faa.gov/)
- [Developer Portal](https://api.faa.gov/)
- [Data Portal](https://www.faa.gov/data)
- [Data Catalog](https://catalog.data.faa.gov/dataset)
- [Open Data](https://ais-faa.opendata.arcgis.com/)
- [Open Data](https://udds-faa.opendata.arcgis.com/)
- [Bulk Download](https://registry.faa.gov/database/ReleasableAircraft.zip)
- [Website](https://registry.faa.gov/aircraftinquiry/)
- [Website](https://www.faa.gov/air_traffic/technology/swim)
- [Website](https://portal.swim.faa.gov/)
- [Website](https://drs.faa.gov/browse)
- [Website](https://adip.faa.gov/agis/public/)
- [Website](https://www.faa.gov/uas/programs_partnerships/data_exchange)
- [LinkedIn](https://www.linkedin.com/company/faa)

## Maintainers

- Kin Lane — kin@apievangelist.com

## Review

See [review.yml](review.yml) for the full switching-cost review: interface shape, second source, exit path, identifier portability, contractual lock-in, access gate and distribution model, with the HTTP status of every URL probed on 2026-07-28.
