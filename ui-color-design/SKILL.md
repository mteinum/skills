---
name: ui-color-design
description: Design, implement, or review color systems for app and web interfaces. Use for palettes, semantic color tokens, light and dark themes, interaction states, contrast, and chart colors. Preserve existing brand and platform conventions; this is not a full accessibility audit or a print color workflow.
---

# UI Color Design

Turn a visual direction into usable color roles, implementations, and evidence. Preserve the product's character and the user's requested scope. A vivid, expressive interface can be appropriate; do not automatically replace it with a neutral template.

## Establish the task

Inspect the relevant screens, theme definitions, components, brand constraints, and supported platforms. Identify the main user task, audience/locales, viewing conditions, and requested appearances. Infer these from the project before asking for missing information.

- **Design:** propose a color direction and show it on representative UI, including meaningful states.
- **Implement:** update the existing theme/component architecture and verify the affected interface.
- **Review:** report evidenced problems with locations and remedies; do not edit the product solely because a review was requested.

For a small fix, examine the affected roles and their consumers. Build a complete palette or theme only when the task needs one.

## Use evidence appropriately

The [source catalogue](references/sources.md) distinguishes standards, platform guidance, practitioner methods, and research. Consult relevant entries when explaining a consequential choice or resolving a conflict. Sources were checked on 2026-10-28; recheck current platform APIs, browser support, and standards when implementing version-sensitive behavior.

Treat research as evidence within its study conditions. Color associations do not establish that a hue causes trust, emotion, or conversion. Harmony schemes and proportions such as 60–30–10 are optional composition heuristics, not accessibility tests or scientifically required ratios.

## Design roles before assigning values

Identify surfaces, content, actions, feedback, selection, and focus. Separate brand expression, semantic status, and data series where they serve different meanings. Reuse the project's token names; otherwise use the role and pairing model in [Implementation](references/implementation.md).

Keep role meanings stable across themes, while allowing their values to change. Pair each filled surface with an intentional foreground. A brand color that works decoratively may need a different tone for a button, link, or small label.

Establish hierarchy with area, placement, typography, and color together. Use accent repetition to make related actions recognizable. Avoid giving unrelated decorative elements the same prominence as the main task unless that is the intended composition.

## Construct and adapt the palette

Use monochromatic, analogous, or complementary relationships as candidate directions. If specifying hue angles, name the color model; named-color examples and different color wheels are not interchangeable.

Separate hue, chroma, and lightness decisions. Oklab/OKLCH can help construct perceptually smoother ramps, but their lightness coordinates do not replace measured contrast. Inspect gamut mapping and the actual output colors on supported targets.

Develop light and dark role mappings deliberately. Review surfaces, foregrounds, elevation, assets, and interactions in each appearance instead of assuming numerical inversion preserves hierarchy. Retain user appearance preferences and platform adaptations. Do not assert that either appearance is universally healthier or more readable.

Use the chart guidance in [Implementation](references/implementation.md#charts-and-data) when color encodes data; an attractive brand palette alone is insufficient.

## Verify in context

Read [Accessibility and validation](references/accessibility-and-validation.md) for thresholds, exceptions, and measurement. Evaluate actual foreground/background pairs and relevant states, including composition over images or translucent surfaces. A single color cannot be certified accessible in isolation.

Check non-color cues for meaning and interaction, keyboard focus, and the affected appearance/accessibility settings. Inspect real text and chart marks at their intended sizes. Automated contrast results, grayscale previews, and color-vision simulations each reveal different problems; none establishes complete accessibility.

## Deliver a usable result

Scale the output to the task. Provide the relevant role mapping or code changes, the rationale for significant choices, and concrete verification evidence. A palette handoff should identify approved pairings and states, not only swatches.

For reviews, include the component/state, observed colors or behavior, user impact, applicable criterion or design rationale, and a practical fix. Distinguish measured failures from hypotheses and untested cases. Report remaining limitations without claiming whole-product compliance from color checks.
