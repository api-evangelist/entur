---
name: entur-purchase-travel-sales-v2
description: Search, reserve, confirm and purchase public transport offers with Entur Sales v2 (OMSA-style processes), then fetch travel documents.
api: openapi/entur-omsa-openapi.yml
operations: [oauthTokenPost, searchOfferHandler, selectOffersHandler, addTravellerHandler, confirmPackageProcessHandler, purchasePackageProcessHandler, purchaseOffersProcessHandler, releasePackageProcessHandler, traveldocumentsCollectionHandler, getPackage, claimRefundProcessHandler, confirmRefundClaimProcessHandler]
generated: '2026-10-09'
method: generated
---
# Purchase travel with Entur Sales v2

Partner API: obtain a token with `oauthTokenPost` (`POST /oauth/token`, `client_credentials`) and send `ET-Client-Name`.

1. **Search** — `searchOfferHandler` (`POST /processes/search-offers/execute`).
2. **Build a package** — `selectOffersHandler` creates a draft package from chosen offers; add people with `addTravellerHandler`.
3. **Confirm and buy** — `confirmPackageProcessHandler`, then `purchasePackageProcessHandler`. For a one-shot buy without a draft, use `purchaseOffersProcessHandler`.
4. **Abandon** — `releasePackageProcessHandler` releases the reservation (use `extendExpiryTimeProcessHandler` if you need more time).
5. **Deliver** — `traveldocumentsCollectionHandler` lists travel documents; `getPackage` reads the package state.
6. **Refund** — `claimRefundProcessHandler` then `confirmRefundClaimProcessHandler` (list options first with `refundOptionHandler`).

Process endpoints are POSTs that change state: do not blindly retry a purchase — re-read the package with `getPackage` before retrying.
