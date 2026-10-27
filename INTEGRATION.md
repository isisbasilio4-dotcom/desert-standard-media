# Growth Strategy Applications — Formspree

Provider endpoint: https://formspree.io/f/mdeeebkl

The website submits all four steps as FormData with Accept: application/json. Success is displayed only after an HTTP success response with Formspree's ok:true acknowledgement. Invalid JSON, rejected responses, network failures, and a 25-second timeout leave answers intact and offer retry. There is no scheduling integration.

The in-flight guard disables submit, Back, Close and current inputs; a completed application cannot be submitted again in the same open page. applicationReference is retained across unchanged retries for tracing, but Formspree server-side idempotency is not assumed. An uncertain timeout followed by retry can produce more than one provider record. No private API credentials are embedded in code.

The privacy notice names Formspree and explains business-fit review and follow-up, with no marketing-email subscription. Personal answers remain in page memory until submitted; they are not written to localStorage. Do not collect patient or medical information.

Owner settings: verify the Formspree notification email and inspect the dashboard for the application marked TEST — Website Integration. Configure domain restrictions and appropriate spam protection in Formspree without disabling active anti-abuse controls. Provider plan limits and archive retention apply. Never delete genuine applications when cleaning up test data.

Checks: automated integration-handler tests passed for loading, duplicate-click suppression, successful acknowledgement, provider rejection, unconfirmed success, network retry, retained answers, and stable retry reference. Browser end-to-end submission is being verified before the main homepage is enabled.
