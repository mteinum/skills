# Submissions and rejections

Use this workflow to turn an implementation assessment into a reviewable submission or a factual response.

## Assemble the review context

Identify the exact build and record what has been checked in that build. Compare it with screenshots, descriptions, privacy declarations, products, and reviewer instructions. Separate unavailable evidence from observed failures.

Prepare the information needed to reach and understand the relevant features: business model, audience, changes, navigation steps, test environments, external-service dependencies, and regional differences. Keep test accounts active for each required role and ensure the backend is available. Put credentials in the designated private App Review information, never in public reports or the repository. For hardware-dependent features, Apple's guidance calls for video showing a physical Apple device interacting with the hardware; a screen recording alone may not establish that interaction. Consult [Complete review](https://developer.apple.com/help/app-review/before-submitting-for-review/complete-review).

Do not fabricate accounts, hardware tests, licenses, or permission from a regulator. If the feature cannot be accessed in the review environment, investigate Apple's documented options and any required prior approval before proposing a substitute demo.

Use [purchase configuration guidance](https://developer.apple.com/help/app-review/before-submitting-for-review/configure-in-app-purchases) when review depends on paid features. Identify the actual account, product, or agreement dependency rather than asking the reviewer to work around a broken flow.

## Investigate a rejection

1. Preserve the original message, guideline numbers, attachments, build/version, device/OS, and reported steps.
2. Reproduce the issue under the closest available conditions. Record any differences in account, region, backend, network, or feature flags.
3. Read the current cited clause and helper guidance. If numbering has changed, state the mapping and preserve the clause Apple actually cited.
4. Determine whether the problem is product behavior, metadata/configuration, reviewer access, missing documentation, or a misunderstanding.
5. Apply authorized corrections and verify the reported path. Explain whether the correction requires a new binary, store metadata, server configuration, or supporting information.
6. Draft a response addressing every cited issue with evidence from the corrected build or the existing behavior.

A failed reproduction does not by itself disprove the rejection. Identify what differs and which evidence would distinguish an intermittent problem from a misunderstanding.

## Choose the appropriate response

For an active submission, use App Store Connect communication to clarify a request or explain the relevant feature with precise steps. Apple's [contact guidance](https://developer.apple.com/help/app-review/after-submitting-for-review/contact-app-review) distinguishes this conversation from formal appeals and expedited-review requests.

An appeal addresses an unresolved disagreement with a rejection or removal after clarification. Requests for more information, review status, or expedition use other routes; correcting and resubmitting an app is also distinct from appealing. Apple's guidance calls for one appeal per rejected or removed app that addresses all cited issues. Use the [App Review Board guidance](https://developer.apple.com/help/app-review/after-submitting-for-review/appeal-to-the-app-review-board) to confirm eligibility and prepare the case.

Do not argue solely from competitors' approvals or business urgency. Link the applicable rule to the app's actual behavior. If the issue is confirmed, focus on the correction; if it is disputed, explain the interpretation and supporting evidence without claiming an assured outcome.

## Draft useful review notes

Adapt this structure to the specific submission, omitting irrelevant fields:

```text
App and build:
Purpose and intended users:
Changes relevant to this review:
Steps to reach and exercise the affected feature:
Account roles and private credential location:
Purchase, hardware, regional, or service dependencies:
Supporting evidence and any known testing limitations:
```

Use the final product's labels and actual navigation. Keep credentials out of the draft when it will be committed or shared publicly.

## Draft a reply or appeal

```text
Submission and guideline:
Our understanding of the reported issue:
Correction made, or reason we believe the existing behavior satisfies the clause:
Exact steps to verify in the identified build:
Supporting evidence:
Specific clarification or reconsideration requested, if needed:
```

Replace every factual field with verified information. Mark missing details clearly instead of filling them with plausible claims. For multiple cited issues, repeat only the issue-specific explanation and evidence.

Drafting a message does not imply permission to send it. When sending, appealing, or submitting is already authorized, finish the concrete draft and required checks, then perform the authorized action. Report the actual result returned by the service; an accepted upload or successful message delivery is not App Review approval.
