---
name: Fetch FAA terminal procedures and VFR/IFR charts
description: >-
  Pull FAA chart products — terminal procedures (dTPP), VFR sectionals, terminal area
  charts and IFR enroute charts — by edition, format and geographic area, including the
  changeset edition that returns only what changed since the previous release.
api: openapi/faa-aeronautic-product-release-api-openapi.yml
operations: [getTPPEdition, getTPPRelease, getSectionalInfo, getSectionalChart, getTACEdition, getTACRelease, getIFREnrouteEdition, getIFREnrouteRelease]
generated: '2026-07-28'
method: generated
source: openapi/faa-aeronautic-product-release-api-openapi.yml
---

# Fetch FAA terminal procedures and VFR/IFR charts

## What this API is

The FAA Aeronautic Product Release API (APRA), **CC0** and **unauthenticated**.

Base URL: `https://external-api.faa.gov/apra`

Seventeen chart product families, each an `/info` edition lookup plus a `/chart`
download. Responses are XML in the `http://arpa.ait.faa.gov/arpa_response` namespace
with no declared schema.

## The shared query vocabulary

The same small enum-constrained parameter set is reused across every family — this is
the one genuinely consistent convention in the FAA REST estate:

- `edition` — `current` | `next` (default `current`). `getTPPRelease` alone also accepts
  `changeset`.
- `format` — a per-product enum. IFR enroute accepts `tiff` (georeferenced) and `pdf`
  (not georeferenced).
- `geoname` — `US` or a full US state name for terminal procedures; a named chart area
  (for example `Seattle`) for sectionals and terminal area charts; `US`, `Alaska`,
  `Pacific` or `Caribbean` for IFR enroute.
- `seriesType` — `Low` | `High` | `Area`, IFR enroute only.

Always call the `/info` operation before the `/chart` operation. `edition=next` returns
`404` until the next edition is staged for release on the 28-day airspace cycle.

## Terminal procedures (dTPP)

1. `getTPPEdition` — `GET /dtpp/info?edition=current&geoname=US`. Edition information is
   identical regardless of geographic area or chart format.
2. `getTPPRelease` — `GET /dtpp/chart?edition=current&geoname=US`.

**Incremental updates:** `getTPPRelease` with `edition=changeset` operates against the
current release and returns only the charts that changed since the previous release.
Use it instead of re-downloading the full set every cycle.

**Size warning:** requesting by US state returns a list of download URLs the FAA's own
description calls "quite extensive". There is no pagination control and no page-size
parameter — budget for one large response, not a paged one.

## VFR sectional charts

1. `getSectionalInfo` — `GET /vfr/sectional/info?edition=current&geoname=Seattle`.
   Observed live 2026-07-28: editionNumber 97.
2. `getSectionalChart` — `GET /vfr/sectional/chart?edition=current&format=...&geoname=...`.

## VFR terminal area charts (TAC)

1. `getTACEdition` — `GET /vfr/tac/info`.
2. `getTACRelease` — `GET /vfr/tac/chart`.

## IFR enroute charts

1. `getIFREnrouteEdition` — `GET /enroute/info?edition=current`.
2. `getIFREnrouteRelease` — `GET /enroute/chart?edition=current&format=tiff&geoname=US&seriesType=Low`.

Use `format=tiff` when you need georeferenced imagery; `pdf` is not georeferenced.

## Error handling

`400` means a parameter value is outside its enum — check `edition`, `format`,
`geoname`, `seriesType` first. `404` means the edition is not released yet or the
requested combination does not exist on the FAA aeronav site. `500` is an internal
service error; retry, since these are read-only GETs.

No error schema, no error code and no `Retry-After` are published. See
`errors/faa-problem-types.yml`.

## Do not use

`getDERSRelease` and `getDERSEdition` are marked `deprecated: true`; the Digital Enroute
Supplement is no longer published and `404` is their only declared response.
