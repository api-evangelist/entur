---
name: entur-shared-mobility-bookings
description: Create and track shared-mobility (one-stop) bookings and operator availability via the Entur shared mobility API.
api: openapi/entur-shared-mobility-openapi.yml
operations: [getAvailability, createOneStopBooking, oneStopEvent, getBooking, getActiveBookings, getBookings, retryFailedPayment, createSupportCase]
generated: '2026-10-09'
method: generated
---
# Shared mobility bookings

1. **Which operators are available** — `getAvailability` (`GET /operators/availability`).
2. **Book** — `createOneStopBooking` (`POST /bookings/one-stop`); push lifecycle events for it with `oneStopEvent` (`POST /bookings/{bookingId}/one-stop/event`).
3. **Track** — `getBooking`, `getActiveBookings` (per customer number) and `getBookings`.
4. **Payment problems** — `retryFailedPayment` (`PUT /bookings/{bookingId}/retry-failed-payment/{recurringPaymentId}`).
5. **Support** — `createSupportCase` (`POST /support`).

Most operations in this spec have no summary; read each operation's schema before calling. Booking creation is a non-idempotent POST.
