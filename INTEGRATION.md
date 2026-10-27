# Application integration — required before production launch

The redesign is preview-only. Keep APPLICATION_ENDPOINT empty until a real backend is configured and tested. The current production homepage and CNAME are preserved while the redesign is on this branch. A clearly labeled preview is available at /preview-redesign/.

## Required destination
Provide a CRM webhook or secure application API controlled by Desert Standard Media. The frontend expects an HTTPS endpoint accepting JSON POST requests with Content-Type: application/json and Idempotency-Key. Permit CORS from https://desertstandardmedia.com (and www if used), including OPTIONS, POST and those headers. Never put API secrets in browser code.

Respond with a 2xx JSON object {"saved":true,"applicationId":"durable-record-id"} only after durable storage. Return the same record on retries with the same idempotency key; enforce uniqueness server-side. A CRM acknowledgement that only queues data is insufficient without durable acceptance. Validate required fields and allowed choices server-side; sanitize text, enforce length limits, rate-limit abuse, and add bot protection appropriate to the provider. Do not collect patient or medical information.

Fields: fullName, businessName, role, websiteOrInstagram, cityState, servicesToPromote, primaryGoal, marketingChallenge, paidAdsStatus, currentMonthlySpend, plannedMonthlyBudget, managementFeeReadiness, startTimeline, email, phone, preferredContactMethod, additionalDetails.

## Configure and verify
Set APPLICATION_ENDPOINT in index.html. Verify a test application appears in the actual destination and only then test success rendering. Verify retries with the same key create only one record; non-2xx, invalid JSON, timeouts and unconfirmed saves retain all answers. Finalize provider-specific privacy disclosures and retention/access settings before collecting real applications. No scheduling button is included because no scheduling integration was provided.

## Motion and accessibility
Canvas terrain has CSS sculpture/static gradients as fallback, pauses offscreen, caps pixel ratio and respects reduced motion. Native dialog provides focus containment and Escape dismissal; answers persist while navigating or closing/reopening, only in page memory. No personal answers are written to localStorage. Refreshing discards them.
