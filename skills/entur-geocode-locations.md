---
name: entur-geocode-locations
description: Resolve free-text places, addresses and stop names in Norway to coordinates and IDs with Entur's Geocoder, or reverse-geocode a coordinate.
api: openapi/entur-geocoder-openapi.yml
operations: [autocomplete, reverse, place]
generated: '2026-10-09'
method: generated
---
# Geocode locations with Entur

Base URL: `https://api.entur.io/geocoder` (open service, NLOD). Send the `ET-Client-Name` header on every request, formatted `<company>-<application>`.

1. **Search by text** — `autocomplete` (`GET /v3/autocomplete`) with the user's text; pick the best match and keep its ID (e.g. an `NSR:StopPlace:` ID for stops) and coordinates.
2. **Look up a known ID** — `place` (`GET /v3/place`) to fetch full details for IDs you already hold.
3. **Coordinate to place** — `reverse` (`GET /v3/reverse`) to find the nearest named places for a lat/lon.

Notes: all three are read-only GETs and safe to retry. Clients moving from Geocoder v1/v2 should read the v2→v3 migration guide (developer.entur.no/docs/open-services/geocoder/migration-v2-v3). Trip planning itself is the Journey Planner v3 GraphQL API, not REST.
