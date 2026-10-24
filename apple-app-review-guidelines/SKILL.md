---
name: apple-app-review-guidelines
description: Assess App Store submission readiness, interpret App Review rejections, implement review-related fixes, and draft review notes or appeals using Apple's current App Review Guidelines. Use for numbered guideline issues, payments, accounts, privacy, content moderation, and submission evidence. Excludes purely visual HIG reviews and does not guarantee approval.
---

# Apple App Review Guidelines

Help the user resolve a concrete App Review question with current policy, evidence from the app, and a verifiable next step.

## Establish the scope

Determine whether the task is a readiness review, a specific rejection, an implementation fix, or preparation of review communications. Keep a narrow request narrow.

Inspect available project files, submission artifacts, and connected App Store information before asking for details. Establish the relevant platform, build/version, distribution channel, storefronts, audience, account model, monetization, and data flows. For a rejection, retain Apple's exact message, cited clauses, submission date, and affected build. Ask only for missing facts that change the conclusion; continue independent work while waiting.

Separate the working tree from the submitted binary and its live configuration. A fix in source does not establish that the reviewed build contains it.

## Verify current policy

Open Apple's [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/) for each new assessment, then read the relevant clauses and linked Apple guidance. Reuse those verified sources during the same assessment unless new information warrants refreshing them. Record the access date and any displayed revision date.

Preserve conditions, exceptions, platform differences, and storefront scope. Reconcile old rejection references with current numbering without rewriting the original message. Consult [Apple developer news](https://developer.apple.com/news/) when a policy change explains a discrepancy.

If live sources are unavailable, clearly identify conclusions as provisional and state which policy could not be verified. Do not present remembered rules, this skill's topic index, or third-party summaries as current authority.

## Load only the relevant references

- [Policy and evidence](references/policy-and-evidence.md): route a general review, locate applicable clauses, and connect findings to evidence.
- [Accounts, payments, and privacy](references/accounts-payments-and-privacy.md): investigate login, deletion, purchase paths, storefront exceptions, data disclosures, tracking, and SDKs.
- [Submissions and rejections](references/submissions-and-rejections.md): prepare reviewer access, validate the submission, investigate a rejection, and draft a reply or appeal.

For interface conventions, use the Apple Human Interface Guidelines skill when available. A HIG assessment does not establish App Review acceptance. Identify alternative-distribution or notarization tasks explicitly and consult the applicable Apple process instead of treating it as a full App Store review.

## Work from evidence to action

1. Trace the relevant user journey and configuration. Inspect code, assets, entitlements, dependency versions, store metadata, backend behavior, and runtime evidence as applicable.
2. Match each suspected issue to the current clause and explain why it applies to this app. Distinguish an explicit requirement from a suggested engineering improvement.
3. Classify the finding as **confirmed issue**, **potential risk**, or **missing evidence**. State what observation would resolve uncertainty. Missing access to App Store Connect is not proof of a configuration error.
4. Implement fixes within the user's authorized scope. Preserve product intent; when policy permits multiple approaches, explain the actual tradeoff before changing the business model.
5. Run focused verification of the affected behavior. Report the build, environment, and paths exercised. Compilation, screenshots, static analysis, and an automated checklist each establish only what they actually inspect.

Never hide functionality, misrepresent data practices, fabricate reviewer evidence, or propose temporary behavior intended to evade review.

## Deliver a usable result

Lead with the outcome for the requested scope. For each material finding include:

- Current guideline number and direct Apple source link.
- Applicability and concrete evidence: file/line, build, screen, configuration, or observed behavior.
- User-visible problem or review risk, with uncertainty stated.
- Smallest appropriate correction and how to verify it.

Finish with remaining evidence gaps and the next submission action, if relevant. Avoid numerical compliance scores and predictions of approval. Apple determines the review outcome.

For communications, provide a concrete draft with verified facts and clearly marked missing details. Send review messages, file appeals, or submit builds only when the user has authorized that action; carry out existing authorization without requesting it again. Keep reviewer credentials and private customer data out of repository files and public reports.
