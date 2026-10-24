# Accounts, payments, and privacy

Load the sections relevant to the app. Confirm current policy before making a product decision.

## Login and account lifecycle

Map each authentication path and determine whether it creates or authenticates the primary account. Under [guideline 4.8](https://developer.apple.com/app-store/review/guidelines/#login-services), assess the equivalent-login criteria and listed exceptions; do not assume every third-party login requires Sign in with Apple.

Then inspect account creation, including web and automatic guest creation. Apple distinguishes deletion from deactivation and expects in-app initiation where its deletion rule applies. A direct deletion webpage can be part of the flow; tvOS has a URL/QR accommodation. Customer-service-only deletion is generally restricted to qualifying regulated cases. Reasonable identity verification and manual processing can be acceptable with clear timing and completion information. Explain required retention rather than promising every record disappears immediately. For Sign in with Apple accounts, inspect token revocation. Subscription cancellation and account deletion are separate; explain continuing billing and the cancellation path. If offering deletion at subscription expiry, retain an immediate-deletion option. Verify the specific circumstances against Apple's [account deletion guidance](https://developer.apple.com/help/app-review/guideline-reference/5-1-1-account-deletion).

Suggested verification: create an account, locate deletion without prior knowledge, complete confirmation, observe the processing result, and inspect the documented retention behavior. Use an authorized test account and appropriate environment. Do not delete a real account merely to complete an audit.

## Classify the purchase before choosing a payment route

Write down:

- What the customer receives and where it is consumed.
- Whether it is digital functionality/content, a physical product, or a service.
- Platform, storefront, account type, and intended audience.
- Where discovery, checkout, access, renewal, and restoration occur.
- Any claimed exception, agreement, or granted entitlement.

Resolve the route against [guidelines 3.1.1–3.1.3](https://developer.apple.com/app-store/review/guidelines/#payments). External purchase rules vary by storefront, including the United States; avoid worldwide claims about prohibition or entitlement requirements.

If the route uses Apple's external purchase mechanisms, read the relevant region's [external purchase documentation](https://developer.apple.com/documentation/storekit/external-purchase), including eligibility, agreements, entitlement, and platform/runtime conditions. A source-code entitlement key is not evidence that Apple granted access. Do not infer a permission for one storefront applies elsewhere, or copy fees and commercial terms from memory.

For in-app purchases, inspect App Store product configuration and test the actual sandbox path. Review uses sandbox transactions with real product information; products need not already be approved to function during review. Check the Paid Apps Agreement status and whether products are ready to submit. Fetch current product information through StoreKit. Explain feature, device, or territory restrictions in review notes. Apple's [purchase configuration guidance](https://developer.apple.com/help/app-review/before-submitting-for-review/configure-in-app-purchases) describes these dependencies.

Local StoreKit configuration tests alone do not establish that App Store Connect products and the server work together. Exercise purchase, interruption, restore, and entitlement delivery where applicable. Use sandbox transactions for verification. Report an agreement or missing entitlement as a dependency; a readiness check does not authorize accepting commercial terms.

For subscriptions, inspect the actual offer, price, duration, trial conversion, delivered benefit, and management path against Apple's [subscription guidance](https://developer.apple.com/app-store/subscriptions/). Compare the paywall with the product returned in the test environment instead of trusting a mockup.

## Trace data before checking declarations

Create a small inventory from the app and its dependencies:

| Data or identifier | Collection point | Recipient | Purpose | Retention | Linked to identity? | Store disclosure |
| --- | --- | --- | --- | --- | --- | --- |

Include embedded web content, analytics, crash reporting, authentication, advertising, and AI providers when present. Inspect configuration and observed behavior, not only package names.

Evaluate these separately:

1. **App privacy details.** Reconcile the app and partners' practices with App Store Connect answers using Apple's definitions of collection, linkage, purpose, and tracking. Apply optional-disclosure exceptions only when all relevant conditions hold. An app without its own backend can still collect through SDKs. See [App privacy details](https://developer.apple.com/app-store/app-privacy-details/).
2. **Tracking permission.** Determine whether behavior meets Apple's tracking definition, including cross-company linkage or data-broker sharing. ATT is not a general-purpose analytics consent prompt, and lack of IDFA access does not establish absence of tracking. See [User privacy and data use](https://developer.apple.com/app-store/user-privacy-and-data-use/).
3. **SDK and build disclosures.** Check the current affected-SDK list, actual dependency versions, privacy manifests, and applicable binary-signature requirements. Repackaged dependencies can still be covered. Read [Third-party SDK requirements](https://developer.apple.com/support/third-party-SDK-requirements/); do not assume every SDK has identical obligations.
4. **AI sharing.** Check disclosure and explicit permission for sharing personal data with third-party AI under [guideline 5.1.2](https://developer.apple.com/app-store/review/guidelines/#data-use-and-sharing).

These mechanisms do not substitute for one another. Trace consent and permission-denial behavior as well as the successful path. If an external service's retention or use is unknown, record that gap rather than inventing a privacy answer. For implementation details such as required-reason APIs, consult the current linked technical documentation before editing declarations.
