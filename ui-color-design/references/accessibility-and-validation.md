# Accessibility and validation

Use the project's accessibility target. For web work without a stated target, use WCAG 2.2 AA color-related criteria as a working baseline and identify that assumption. For native apps, combine applicable platform guidance with these useful checks; do not describe a color review as native-app certification.

## Contrast criteria

| Content | WCAG 2.2 baseline | Scope |
| --- | --- | --- |
| Ordinary text, including informative placeholder text | 4.5:1, SC 1.4.3 AA | Actual foreground/background pair |
| Large text | 3:1, SC 1.4.3 AA | At least 18 pt regular or 14 pt bold: 24 CSS px or about 18.67 CSS px; not device pixels |
| Required control/state cues and meaningful graphical parts | 3:1, SC 1.4.11 AA | Relevant adjacent colors; not every decorative border |

Logotypes, incidental/decorative text, and inactive controls have scoped exceptions. Supporting explanations and other active content are not exempt merely because they sit near a disabled control. Do not round a failing ratio up to a passing threshold. Leave practical margin for delicate typography. [Text criterion](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html), [non-text criterion](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

Test each interaction state against its own surrounding colors. WCAG 1.4.11 does not require a 3:1 difference between hover and default states that are not simultaneously adjacent. [State guidance](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

## Focus and visible meaning

At AA, keyboard focus must be visible (2.4.7), the focused component must not be entirely hidden by author-created content (2.4.11), and author-styled indicators must satisfy applicable non-text contrast. At AAA, 2.4.13 adds an indicator-area target equivalent to a 2 CSS px perimeter and a 3:1 change between the same focused/unfocused pixels, subject to its exceptions. Do not merge these into a single AA rule. [WCAG 2.2](https://www.w3.org/TR/WCAG22/), [Focus Appearance](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance).

Provide visible alternatives when identifying a hue conveys meaning: error text with an icon, selection with a checkmark, directly labeled series, or distinguishable line styles. Screen-reader-only text does not solve this visual problem. Prefer persistent underlines for inline links as a straightforward design choice, rather than relying on color discrimination. [Use of Color](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html).

## Measure the actual composition

Use a reliable contrast tool appropriate to the color space and rendering pipeline. For opaque sRGB pairs, WCAG contrast uses linearized relative luminance, not RGB averages, HSL lightness, or OKLCH lightness. APCA can supply supplementary information, but is not the WCAG 2.2 conformance calculation. [WCAG definitions](https://www.w3.org/TR/WCAG22/#dfn-relative-luminance).

Resolve foreground opacity, ancestor opacity, backgrounds, overlays, and relevant states before measurement. For gradients, photos, blur, and moving content, inspect the lowest-contrast relevant regions and plausible content changes. Add a stable backing surface or scrim where needed, then recheck. Report uncertainty if the evidence is only a screenshot or the background cannot be reconstructed. Prefer resolved styles over sampling antialiased glyph edges.

Record results in a compact matrix:

| Component/state | Appearance | Foreground | Background/composition | Ratio/tool | Criterion | Result |
| --- | --- | --- | --- | --- | --- | --- |

Populate only measured results. State when a result covers opaque sRGB pairs only; do not silently claim verification of Display P3, transparency, or variable imagery.

## Check the interface

Choose checks proportional to the changed surface:

- Inspect actual text, controls, status, and chart marks at intended sizes in affected themes and states.
- Navigate with a keyboard and verify focus remains identifiable through scroll and overlays.
- Check meaningful information without hue identification. Grayscale and protan/deutan/tritan simulations are diagnostic aids, not substitutes for user testing or proof of accessibility.
- Exercise supported increased-contrast settings, forced colors on the web, and relevant native accessibility appearance settings. User-selected palettes may change or remove authored colors.
- Use representative users and tasks when validating an important new direction. Compare errors, comprehension, or task completion separately from preference ratings.

Return a specific finding, remedy, and evidence for each actionable issue. State what was not tested. Passing these checks does not establish compliance with WCAG criteria outside the assessed scope.
