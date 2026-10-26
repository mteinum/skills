---
name: apple-app-store-assets
description: Create, review, and prepare App Store screenshots, app previews, icons, product page headers, search artwork, and In-App Event media using Apple's asset best practices and current export specifications. Use for asset briefs, storyboards, localization, crop checks, and export validation. Excludes general in-app interface design and full App Review readiness audits.
---

# Apple App Store Assets

Turn a requested asset brief, production task, or review into concrete deliverables grounded in the app and Apple's current guidance.

## Establish the asset and destination

Inspect available captures, artwork, project files, and store metadata. Identify the app version, placement, platform/device family, orientation, locales, and requested output format. Ask only for missing details that change the work. Keep a request for one asset scoped to that asset.

Separate app-in-use screenshots and app previews from brand-oriented creative assets. A cinematic marketing video cannot automatically serve as an app preview. For production work, use authentic captures for depicted UI; mark proposed screens as concepts until they exist in the app. Generated illustration may support creative artwork, but must not masquerade as captured functionality.

## Consult current Apple sources

Open [App Store asset best practices](https://developer.apple.com/app-store/asset-best-practices/) and the relevant specification for each new assignment. Record the access date with material requirements; reuse verified sources during the assignment. This skill was researched on 2026-10-26 and is a workflow, not a frozen specification.

- For screenshots or app previews, read [Screenshots and previews](references/screenshots-and-previews.md).
- For headers, search artwork, or In-App Events, read [Creative assets and events](references/creative-assets-and-events.md).
- For icons, consult [App icons in the HIG](https://developer.apple.com/design/human-interface-guidelines/app-icons) and the linked current production guidance. Assess recognition at small sizes as well as the store presentation.

Distinguish an upload requirement, an App Review rule, and a creative recommendation. Verify relevant clauses in [Accurate Metadata, section 2.3](https://developer.apple.com/app-store/review/guidelines/#accurate-metadata) before calling something a policy violation. If a source is unavailable, identify the unverified point and continue work that does not depend on it. Do not invent dimensions, safe-area coordinates, or approval outcomes.

## Apply shared creative and content checks

From Apple's [asset best practices](https://developer.apple.com/app-store/asset-best-practices/):

- Keep the experience recognizable, with a coherent palette, typography, and tone across the set.
- Exclude specific prices, discounts, website URLs, copyright symbols, and Apple recognition badges or claims such as App of the Day. Check unsupported accolades and other-platform references against the applicable policy.
- Use concise, localized copy, inclusive imagery, and a clear focal point. Protect essential content from cropping using the applicable template.
- Choose an informative poster frame. Make video understandable without sound, allow time to follow actions, and avoid jarring cuts or loop transitions.

Under [App Review section 2.3](https://developer.apple.com/app-store/review/guidelines/#accurate-metadata), verify that assets reflect available functionality, disclose when featured content requires an additional purchase, use material the developer has rights to, and show fictional account data. Store metadata must suit a 4+ audience even when the app has a higher age rating. Preserve policy exceptions, including the approved-interactive-functionality exception for other-platform references.

## Produce and verify

For a brief or storyboard, map each asset to its intended message, source capture/artwork, copy, locale, and placement. For production, preserve editable masters and create clearly named exports that identify their destination and variant.

Inspect rendered exports, not just source files. Check actual dimensions, file type, alpha, and applicable video properties with available media tools. Review legibility at store display size, crop boundaries, translated text, screenshot order, poster frame, and full video playback. Match technical checks to the exact asset type; a passing image check says nothing about a video's encoding.

Use App Store Connect's preview when access is available. Otherwise provide local previews and state that store rendering remains unverified. For an authorized upload or placement change, consult [Manage your App Store assets](https://developer.apple.com/help/app-store-connect/manage-app-information/manage-your-app-store-assets); distinguish uploaded, approved, assigned, and published states. Creating assets alone does not authorize publishing them. Honor existing authorization without asking again.

Deliver the requested files or review with the important findings first. Tie each issue to a file/frame, its source-backed requirement or design rationale, and a concrete correction. Report what was visually and technically checked and any remaining evidence gaps. Do not promise acceptance, featuring, or conversion gains.
