---
name: Check US airport delays and ground stops
description: >-
  Read the FAA's live national airport delay picture — ground delay programs, ground
  stops, arrival/departure delays and closures — and drill into one airport by IATA
  code. No credential required.
api: openapi/faa-airport-status-web-service-openapi.yml
operations: [getDelays, getAirportStatus]
generated: '2026-07-28'
method: generated
source: openapi/faa-airport-status-web-service-openapi.yml + conventions/faa-conventions.yml
---

# Check US airport delays and ground stops

## What this API is

The FAA Airport Status Web Service (ASWS) publishes the delay picture for roughly 40
major US airports, sourced from fly.faa.gov. It is **Creative Commons Zero (CC0)** and
answers **unauthenticated** — verified HTTP 200 on 2026-07-28.

Base URL: `https://external-api.faa.gov/asws/api`
(alternate: `https://external.apic4e.faa.gov/asws/api`)

> The harvested OpenAPI declares bare hosts without the `/asws/api` base path. A client
> generated straight from the spec will 404. Use the base URL above.

## Setup

Nothing. No API key, no account, no `Authorization` header. The FAA's published plan for
this API is a `KEY_LESS` plan.

Ask for `application/json` or `application/xml` — both are declared on every response.

## Step 1 — get the national picture

Call `getDelays` — `GET /api/airport/delays`. No parameters.

It returns a `Delays` object with four parallel collections:

- `GroundDelays[]` — `{airport, avgTime, reason}`
- `GroundStops[]` — `{airport, endTime, reason}`
- `ArriveDepartDelays[]` — `{airport, minTime, maxTime, reason}`
- `Closures[]` — `{airport, reason, reopen}`

`airport` in every one is an **IATA three-letter code**, so you can join straight into
step 2 and into any other aviation dataset.

## Step 2 — drill into one airport

Call `getAirportStatus` — `GET /api/airport/status/{airportCode}` where `airportCode` is
the IATA code.

It returns an `AirportStatus`: `name`, `city`, `state`, `icao`, `iata`,
`supportedAirport`, `delay` (boolean), `delayCount`, a `status[]` array of `Status`
objects (`type`, `reason`, `avgDelay`, `minDelay`, `maxDelay`, `trend`, `endTime`,
`closureBegin`, `closureEnd`) and a `weather` object.

Check `supportedAirport` before trusting an empty result — an unsupported airport is not
the same as an airport with no delays.

## Error handling

There is no RFC 9457 problem document. Error responses are bare status codes with no
body schema (see `errors/faa-problem-types.yml`).

- `404` on `getAirportStatus` — "Delays are available only for major United States
  airports." The code is outside the supported set. Do not retry; fix the code.
- `404` on `getDelays` — the upstream fly.faa.gov dependency is unavailable. Retry.
- `500` on `getDelays` — fly.faa.gov returned an error. Retry.

Both operations are GETs, so retries are safe. There is no published rate limit for this
API and no `RateLimit` headers, so back off politely on your own schedule.

## Supported airports

BOS, LGA, TEB, EWR, JFK, PHL, PIT, IAD, BWI, DCA, RDU, CLT, ATL, MCO, TPA, FLL, MIA,
DTW, CLE, MDW, ORD, IND, CVG, BNA, MEM, STL, MCI, MSP, DFW, IAH, DEN, SLC, PHX, LAS,
SAN, LAX, SJC, SFO, PDX, SEA.

## Related surfaces

- `https://nasstatus.faa.gov/api/airport-status-information` — the same national picture
  as XML, unauthenticated, no spec.
- `https://tfr.faa.gov/tfrapi/exportTfrList` — active Temporary Flight Restrictions as
  JSON, unauthenticated, no spec.

Neither has an OpenAPI, so neither is used in this skill.
