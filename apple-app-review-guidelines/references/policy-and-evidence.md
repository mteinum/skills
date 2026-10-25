# Policy and evidence

Use this reference for a readiness assessment or to determine which policy governs a reported issue. This is a routing aid, not a replacement for the live rules.

## Find the applicable guidance

Start with the [current guidelines](https://developer.apple.com/app-store/review/guidelines/). The source was checked on 2026-10-25 and displayed an update date of 2026-10-16; verify it again for a new assessment.

| Topic | Starting clauses |
| --- | --- |
| Content and user-generated content | 1.1–1.2 |
| Children | 1.3, 5.1.4 |
| Physical harm and health data | 1.4, 5.1.3 |
| Completeness and metadata | 2.1, 2.3 |
| Hidden or undocumented functionality | 2.5.19; review notes under 2.3.1 |
| Compatibility and software behavior | 2.4–2.5 |
| Purchases and business models | 3.1–3.2 |
| Copycats, utility, and spam | 4.1–4.3 |
| Extensions and remotely offered software | 4.4, 4.7 |
| Login services | 4.8 |
| Data practices | 5.1 |
| Intellectual property | 5.2 |
| Gambling, VPNs, and device management | 5.3–5.5 |
| Developer conduct | 5.6 |

Read the complete applicable subsection, including cross-references. Consult Apple's [review help](https://developer.apple.com/help/app-review/) for operational explanations. Do not turn the entire table into mandatory findings when only one topic is relevant.

## Build an evidence trail

Use the following as an investigation method, not a list of additional Apple requirements.

| Evidence | Useful checks | Limit |
| --- | --- | --- |
| Project and source | Entry points, feature flags, permission requests, purchase and account flows | May differ from the submitted build |
| Build artifact | Version, configuration, dependencies, signing and entitlements | Does not prove a service works |
| Runtime walkthrough | Reproduction steps, device/OS, account role, error and empty states | Covers only exercised paths |
| App Store configuration | Metadata, products, territories, privacy answers, review information | Can be unavailable or change independently |
| Backend and external services | Availability, regional routing, account lifecycle, authorization | Local mocks do not establish production behavior |
| Product documentation | Audience, intended use, licenses, operational commitments | Claims need supporting evidence |

Record where evidence came from and which build or environment it describes. Use available read-only tools first. Do not search unrelated credentials or customer records to fill gaps.

Select the journeys that determine this assessment: first launch, authentication, the primary task, purchase/restore, subscription management, account deletion, permission denial, or content reporting. Add failure cases where they reveal the suspected issue. Explain untested branches instead of labeling every untested feature defective.

For UGC, health, children, regulated products, or specialized entitlements, inspect the actual audience, service, and implementation. Read the relevant policy and supporting Apple documentation before prescribing safeguards or making an eligibility claim.

## Check review integrity and remote configuration

Use [guideline 2.5.19](https://developer.apple.com/app-store/review/guidelines/#software-requirements) for hidden, dormant, or undocumented functionality. Apple's [2026-10-16 update](https://developer.apple.com/news/?id=92th7e5i) explains that this longstanding policy was formerly covered by 2.3.1. Keep the original clause in historical rejection records.

When the app uses conditional functionality, inspect the submitted build and applicable server configuration:

- Trace feature flags, remote content, embedded web flows, and scheduled activation after approval.
- Check whether IP ranges, location, device signals, account roles, or acquisition channels identify reviewers and conceal behavior from them.
- Compare review access with ordinary free and paid user journeys. Record the product reason for each difference and how the reviewer can exercise the relevant behavior.
- Verify that review notes describe new functionality and its access conditions, and that post-approval configuration does not introduce concealed functionality.

Treat these as investigation checks, not proof that every feature flag or regional difference violates policy. Distinguish documented eligibility, authorization, and operational controls from deliberate review evasion; do not prescribe removing all flags. Make functionality available for review through an appropriate documented path, without weakening production authorization.

For a notice citing Section 3.2(f), read the current [Apple Developer Program License Agreement](https://developer.apple.com/support/terms/apple-developer-program-license-agreement/) and the specific notice. Distinguish that agreement provision from App Review Guideline 3.2. Do not infer Apple's internal detection methods, enforcement thresholds, linked-account penalties, or appeal deadlines from third-party articles. Report only what the applicable Apple sources and case evidence establish.

## Report findings precisely

Suggested finding format:

```text
Status: confirmed issue / potential risk / missing evidence
Scope: platform, storefront, build, account role
Guideline: number, title, Apple link, date checked
Evidence: artifact or reproduction steps and actual result
Reason: how this evidence relates to the applicable wording
Correction: concrete change or information needed
Verification: expected result and the check that establishes it
```

Order findings by their impact on the requested submission. Keep implementation quality suggestions separate from explicit policy findings. If the evidence does not establish a violation, report the unresolved question and the smallest check needed.

A review of repository files cannot establish the accuracy of unavailable store declarations, approval of an entitlement, ownership of content, or legal eligibility. Identify the particular missing evidence instead of issuing a blanket verdict.
