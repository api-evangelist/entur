---
name: entur-look-up-stop-places
description: Read stop places, quays, parkings and fare zones from the Norwegian Stop Place Register (NSR).
api: openapi/entur-stop-place-v1-read-openapi.yml
operations: [getStopPlaces, getStopPlaceById, getStopPlaceChildren, getStopPlaceByQuayId, getQuayById, getParkingByStopPlaceId, getScheduledStopPointsForStopPlace, getFareZones, getFareZoneById]
generated: '2026-10-09'
method: generated
---
# Look up stop places in the Stop Place Register

1. **Find stop places** — `getStopPlaces` (`GET /stop-places`) to list stop places, or `getStopPlaceById` (`GET /stop-places/{id}`) when you have an NSR ID such as `NSR:StopPlace:337`.
2. **Drill into the stop** — `getStopPlaceChildren` for child stop places, `getQuayById` for a platform/quay, `getStopPlaceByQuayId` to go from a quay back to its stop place.
3. **Related data** — `getParkingByStopPlaceId` for parking, `getScheduledStopPointsForStopPlace` for the scheduled stop points that timetables reference.
4. **Fare zones** — `getFareZones` / `getFareZoneById`. The tariff-zone operations (`getTariffZones` …) are marked deprecated in the spec; prefer fare zones.

All operations are read-only GETs; `/versions` sub-resources return historical versions of each entity.
