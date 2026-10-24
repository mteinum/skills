---
name: develop-iphone-duo-apps
description: Develop or adapt iOS apps for iPhone Duo using SwiftUI or UIKit. Use for dual-display resizing, fold-aware layouts, reserved regions, vertical bars, camera transitions, and Duo compatibility reviews or testing. Excludes device mockups and promotional animations.
---

# Develop iPhone Duo apps

Build a continuous iPhone experience across closing, opening, folding, rotation, and multitasking. Preserve the app's product, architecture, and deployment targets unless the requested change requires otherwise.

## Establish the implementation context

Inspect the app target, UI framework, navigation hierarchy, state ownership, minimum OS, selected Xcode/SDK, and available test devices. For an existing app, reproduce the affected flow before choosing a replacement container. For a new app, use its requested stack; SwiftUI is a reasonable default when none is specified. For hybrid apps, identify the native integration points without requiring a rewrite.

Read the relevant sections of Apple's [design guide](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo) and [engineering overview](https://developer.apple.com/documentation/technologyoverviews/preparing-your-app-for-iphone-duo). If a documentation page only returns a JavaScript shell, follow its Markdown link; these pages expose an equivalent URL ending in `.md`.

The references were checked on 2026-10-24. Before writing calls to a new API, confirm its declaration and availability in current Apple documentation and the selected SDK. A runtime availability check does not make a symbol compile against an older SDK. Isolate newer declarations in appropriately annotated types or functions, provide a usable fallback for supported older systems, and compile both paths. Do not raise the minimum OS just to avoid an availability error.

## Choose the smallest useful adaptation

- Base layout on the containing scene/view, size classes, safe areas, and layout margins. Avoid device-model branches, screen-sized constants, or treating orientation or phone/tablet idiom as a substitute for actual space.
- Preserve navigation selection, drafts, scroll position, focus, and ongoing work across transitions. As an implementation strategy, keep durable state above any layout branches that replace view identity; avoid restarting tasks merely because the available space changed.
- Prefer the app's system navigation and bar containers. Select a navigation split view for hierarchical content; consider an arrangement view for two related content surfaces. Read [layout and bars](references/layout-and-bars.md) before choosing an arrangement or handling reserved regions yourself.
- Keep the same actions reachable in each pose. Extra room can reveal context, but a small window must still support the task. Avoid separate feature sets for the inner and outer displays.
- Keep adjustments near the fold modest. Preserve familiar control locations and content hierarchy. Do not infer a hinge angle or invent a device-posture API when available geometry and documented regions solve the problem.

The display and interaction recommendations above follow Apple's [Duo design guidance](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo); the state-ownership strategy is this skill's engineering recommendation.

## Implement the relevant path

Read only the supporting guidance needed for the task:

| Work | Reference |
| --- | --- |
| Resizing, arrangement containers, custom geometry, navigation, toolbars, tabs, sheets | [Layout and bars](references/layout-and-bars.md) |
| Camera selection, mirroring, or camera content on the outer display | [Camera behavior](references/camera.md) |
| Compatibility review, transition testing, or verification of a change | [Validation](references/validation.md) |

Make targeted changes in the existing app. Do not add camera accessories, a new navigation architecture, or a general layout framework unless the requested behavior needs them. For games and immersive canvases, preserve interaction scale while adapting the viewport; consult the design guide's game guidance when aspect ratio or letterboxing becomes relevant.

## Verify and deliver

Build the affected target with a concrete available destination. Exercise the changed flow through live size and pose transitions, using the relevant rows of the validation matrix. For an app-wide Duo readiness request, cover the full applicable matrix.

Report the code changed, behavior verified, Xcode/SDK and device/runtime used, and any remaining hardware or toolchain gap. Distinguish compilation, simulator behavior, and physical-device validation. A successful build or resized screenshot alone does not establish Duo compatibility.
