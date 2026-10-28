# Implementation patterns

These are synthesis patterns to adapt to the existing project, not a required token format or palette.

## Roles and pairings

Separate primitive values from semantic roles and, when useful, component bindings. A small interface may need only semantic roles. Keep existing naming if it is coherent. [Carbon](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview) demonstrates the architecture; [Material](https://developer.android.com/develop/ui/compose/designsystems/material3) demonstrates container/foreground pairing.

| Role family | Illustrative names | Pairing/behavior to specify |
| --- | --- | --- |
| Surfaces | `surface.canvas`, `surface.panel`, `surface.raised` | Which text/icons can appear on each surface |
| Content | `text.primary`, `text.secondary`, `icon.default` | Allowed surfaces; secondary text remains readable |
| Actions | `action.primary`, `onAction.primary`, `link.default` | Normal, hover where relevant, pressed, focus, disabled |
| Feedback | `status.error`, `status.warning`, `status.success`, `status.info` | Foreground, container, and visible label/symbol |
| Structure | `border.subtle`, `border.control`, `focus.ring` | Decorative separation versus essential identification |
| Selection | `selection.container`, `selection.content` | Persistent indication distinct from transient hover |
| Data | `data.category.*`, `data.sequential.*`, `data.diverging.*` | Data meaning and stable mapping across views |

Equal values do not imply equal roles: an error and a brand accent can share a hue while retaining different tokens and visible meanings. Do not create speculative roles the product does not use.

For each relevant component, record the foreground/background combination for normal, selected, validation, and interaction states. Reuse shared roles where behavior is shared; introduce a component-specific binding only when it solves a real dependency.

## Palette and hierarchy decisions

Choose the desired character from the product context, then evaluate it on representative screens. Hue can distinguish families; lightness establishes much of the readable separation; chroma changes intensity. These controls interact, and neighboring colors affect their appearance.

A ramp should have useful values for actual roles rather than merely equally spaced numbers. Test very light accents with dark foregrounds as candidates, rather than assuming white button text. [Radix](https://www.radix-ui.com/colors/docs/palette-composition/understanding-the-scale) illustrates purposeful steps and foreground exceptions.

When using harmony geometry, select a declared hue model: a triad uses three hue positions separated by 120 degrees within that model; a split complement uses the two neighbors of the opposite hue. Those relations suggest compositions, not measured contrast. Adjust lightness/chroma and color area to fit the interface rather than preserving geometry at the cost of legibility.

Oklab/OKLCH is useful for authoring ramps and gradients. Check destination gamut and interpolation behavior; equal coordinate increments do not guarantee equal discernibility in every component. Use the existing color library when it supports the needed conversions. [Oklab](https://bottosson.github.io/posts/oklab/), [CSS Color 4](https://www.w3.org/TR/css-color-4/).

## Web

Expose semantic roles through the project's CSS variables or theme layer. Override role values for supported appearances while keeping component references stable. A component should consume an approved pair, for example `background: var(--action-primary)` with `color: var(--on-action-primary)`; those variables require measured values from the project's theme.

Honor the OS preference when no explicit user choice is set. Coordinate the `color-scheme` property with the implemented appearance so native controls fit. It does not recolor custom components automatically. Check embedded content, icons, form controls, selection, and autofill when affected.

Test forced-colors mode and use system colors where needed. Borders/outlines may survive where decorative shadows or fills do not. Avoid applying `forced-color-adjust: none` globally; narrowly retained color needs a reason and usable alternatives. [CSS Color Adjustment](https://www.w3.org/TR/css-color-adjust-1/).

Check actual browser targets before shipping newer color syntax. Where a fallback is needed, preserve an approved sRGB result. A successful parse does not establish appropriate gamut mapping or contrast.

## Apple platforms

Use semantic system colors in their intended roles and adaptive named assets for custom colors. Check custom foregrounds on system materials with actual content behind them. Test appearance and increased contrast; avoid freezing a dynamic system color into one resolved RGB value. Verify API availability in the project's SDK and deployment target. [Apple Color](https://developer.apple.com/design/human-interface-guidelines/color).

## Android

Use Material color roles and the corresponding `on…` roles through the existing theme. Decide whether dynamic color fits product requirements; where used, account for supported OS versions and fallback schemes. Verify custom brand/status/chart colors alongside the dynamically chosen scheme. [Material 3 in Compose](https://developer.android.com/develop/ui/compose/designsystems/material3).

## Charts and data

| Data/task | Candidate encoding | Check |
| --- | --- | --- |
| Unordered categories | Qualitative hues with similar visual prominence | Distinct at real mark sizes; stable category mapping |
| Low-to-high magnitude | Sequential scale with ordered lightness | No unintended reversals or apparent boundaries |
| Deviation about a meaningful value | Diverging scale centered on that value | Center and both directions are clear |
| Cyclic quantities such as direction | Cyclic scale | Endpoints join without an artificial discontinuity |

Use legends or direct labels and visible alternatives such as symbols or line patterns where hue alone carries identity. Do not assume a palette's color-vision-friendly label covers every series count and background. Reduce visible categories, group, or offer filtering when distinctions become unreliable; there is no universal maximum count that works for every chart.

Check on the actual plot background with the intended line width/point size, relevant themes, and color-vision simulations. Continuous scales need perceptual ordering; requiring 3:1 between every infinitesimally adjacent gradient sample is not a useful interpretation of chart accessibility. Evaluate essential marks, boundaries, labels, and other cues against the applicable criterion.

Sources: [ColorBrewer scheme selection](https://colorbrewer2.org/learnmore/schemes_full.html), [Szafir's mark-perception experiments](https://danielleszafir.com/colordiff_vis2017.pdf), [Crameri et al. on scientific color maps](https://www.nature.com/articles/s41467-020-19160-7), [non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).
