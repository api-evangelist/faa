---
name: Track and download the NASR 28-day subscription
description: >-
  Poll the FAA's 28-day airspace (AIRAC) cycle for a new NASR subscription edition and
  download it only once it is actually published. The canonical bulk-export path out of
  any commercial redistributor of FAA aeronautical data.
api: openapi/faa-aeronautic-product-release-api-openapi.yml
operations: [getNASREdition, getNASRSubscription]
generated: '2026-07-28'
method: generated
source: openapi/faa-aeronautic-product-release-api-openapi.yml + lifecycle/faa-lifecycle.yml
---

# Track and download the NASR 28-day subscription

## What this API is

The FAA Aeronautic Product Release API (APRA) publishes chart and aeronautical data
products. It is **Creative Commons Zero (CC0)** and answers **unauthenticated** — the
FAA's published plan for it is a `KEY_LESS` plan.

Base URL: `https://external-api.faa.gov/apra`

The National Airspace System Resource (NASR) subscription is the FAA's full
aeronautical database, republished every 28 days on the airspace (AIRAC) cycle.

## The one convention that matters

Every APRA product family has **two** operations: an `/info` edition lookup and a
`/chart` download. **Always call `/info` first.** The FAA stages `next` editions before
they are released, and `edition=next` returns `404` until the edition actually
publishes. Polling `/chart` directly wastes calls and gives you no way to tell "not yet
published" from "gone".

## Step 1 — check the current edition

Call `getNASREdition` — `GET /nfdc/nasr/info?edition=current`.

`edition` accepts `current` or `next`; omitted, it defaults to `current`.

The response is XML in the FAA-proprietary namespace
`http://arpa.ait.faa.gov/arpa_response`. The spec declares `content: {}` for every
response, so there is no schema — parse the edition number and edition date out of the
`arpa_response` document.

Observed live on 2026-07-28: edition `7`, edition date `07/09/2026`.

## Step 2 — watch for the next edition

Call `getNASREdition` with `edition=next`. Poll on a daily cadence as the current
edition ages toward its 28-day boundary.

- `404` — the next edition is not staged yet. This is the normal, expected answer for
  most of the cycle. Keep polling.
- `200` — the next edition is published. Record its edition date and move to step 3.

## Step 3 — download

Call `getNASRSubscription` — `GET /nfdc/nasr/chart?edition=current` (or `next` once it
is published). It returns the download link for the NASR subscription ZIP.

Store the edition number and edition date alongside the file. That pair, not an API
version, is the FAA's real version identifier — there is no versioning policy and no
`Sunset` header anywhere in the estate.

## Error handling

Every APRA operation declares the same four responses, all with no body schema:

- `200` — OK
- `400` — "Illegal arguments provided to service. One or more of the service parameter
  values is invalid." Check that `edition` is exactly `current` or `next`.
- `404` — "Requested edition has not been released for download or could not be found
  on the FAA aeronav web site." On `edition=next` this is a normal not-yet state, not a
  failure.
- `500` — internal service error. Retry; these are read-only GETs so retries are safe.

There is no RFC 9457 problem document, no error code and no `Retry-After`. See
`errors/faa-problem-types.yml`.

## Other product families on the same pattern

`getTPPEdition`/`getTPPRelease` (terminal procedures), `getSectionalInfo`/
`getSectionalChart`, `getTACEdition`/`getTACRelease`, `getIFREnrouteEdition`/
`getIFREnrouteRelease`, `getCIFPEdition`/`getCIFPRelease`, `getDDOFEdition`/
`getDDOFRelease`, `getGOMEdition`/`getGOMRelease`, `getOceanicRouteEdition`/
`getOceanicRouteChart`, `getIfrPlanningInfo`/`getIfrPlanningChart`,
`getSupplementEdition`/`getSupplementRelease`, `getGrandCanyonEdition`/
`getGrandCanyonRelease`, `getHelicopterEdition`/`getHelicopterRelease`,
`getGulfCoastEdition`/`getGulfCoastRelease`, `getProductEdition`/`getProductRelease`.

**Do not use `getDERSEdition` or `getDERSRelease`.** Both are marked `deprecated: true`
and `404` is their only declared response — the Digital Enroute Supplement is no longer
published by the FAA.
