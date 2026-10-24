---
name: apple-human-interface-guidelines
description: Apply Apple's Human Interface Guidelines when designing, implementing, or reviewing interfaces for iOS, iPadOS, macOS, watchOS, tvOS, or visionOS. Use for platform conventions, navigation, components, visual hierarchy, accessibility, and interaction design. HIG reviews do not establish App Store approval.
---

# Apple Human Interface Guidelines

Turn Apple's HIG into concrete design and implementation decisions for the user's actual product. Preserve the requested platform, framework, brand, and task scope.

## Establish the context

Determine the target platform, supported OS versions, input methods, user task, and available evidence. Inspect the relevant screen, flow, design file, or source code before prescribing changes. Infer context from the project where possible; ask only when an unresolved choice would materially change the result.

Match the requested work:

- **Design:** propose an information hierarchy, interaction model, and appropriate components, including meaningful non-happy-path states.
- **Implement:** make the requested UI changes in the existing stack and verify the resulting behavior.
- **Review:** identify evidenced problems and practical fixes. A review request alone does not call for editing the app.

For a small change, examine the affected surface and dependencies. A full-product audit is appropriate only when requested or needed to resolve a problem that crosses screens.

## Ground decisions in current guidance

Start with the relevant platform in [Platform guide](references/platform-guide.md), then read the Apple pages linked from the applicable sections of [Patterns and foundations](references/patterns-and-foundations.md). Do not load the entire HIG for every task.

Use the [HIG index](https://developer.apple.com/design/human-interface-guidelines/) to find topics beyond this skill. These references were checked on 2026-10-24; consult current pages for changing component behavior, visual treatments, and numerical specifications.

If an Apple page returns a JavaScript shell, follow its Markdown link. The index has a Markdown version at `https://developer.apple.com/design/human-interface-guidelines.md`; individual articles use their page URL followed by `.md`. Confirm that the response contains the expected article body, not just HTML or an error page. If live access fails, use available evidence, identify which guidance remains unverified, and continue work that does not depend on it.

Read the platform-specific section of a component page before generalizing a recommendation. Preserve qualifiers such as "consider" and "in general." Cite the specific page supporting a consequential recommendation, and distinguish Apple's guidance from your own design judgment. If guidance appears inconsistent, explain the scope difference or uncertainty instead of inventing a universal rule.

## Make platform-appropriate choices

Use Apple's [design principles](https://developer.apple.com/design/human-interface-guidelines/design-principles) to resolve tradeoffs around the person's task, control, recoverability, familiarity, and context. They are decision criteria, not a mandatory visual template.

Prefer appropriate system components when they provide the needed behavior. Preserve useful brand expression in content and meaningful customization. Do not restyle every screen or migrate frameworks simply to make an app appear more Apple-like.

For dimensions, distinguish platform, default versus minimum, visible artwork versus hit area, and points versus rendered pixels. Verify the applicable table and actual implementation before reporting a violation. Do not impose one touch-target, spacing, font, corner-radius, tab-count, or contrast rule on every platform and component.

A HIG recommendation is not an API declaration. When implementing it, verify the relevant SwiftUI, UIKit, AppKit, or other framework symbol and its availability in the selected SDK. Keep supported older-OS behavior usable; a runtime availability guard cannot make an older SDK recognize a new symbol.

## Validate and communicate

Use [Review and validation](references/review-and-validation.md) for evidence standards, priorities, and checks proportional to the change. Test the task and relevant transitions, including accessibility and alternate input where affected.

For design work, explain the proposed behavior and why the selected pattern fits. For implementation, summarize changes and actual verification. For reviews, lead with actionable findings, locations, user impact, source, and a concrete remedy; separate observations from hypotheses.

State which platforms, screens, states, and interaction modes were assessed. Avoid unsupported claims of complete HIG compliance, accessibility certification, or App Store acceptance. If no actionable issue is supported by the evidence, say so without manufacturing findings.
