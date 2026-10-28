# Annotated source catalogue

Checked 2026-10-28. This is a targeted evidence review, not a systematic literature review. Summaries are original paraphrases. “Skill use” is the synthesis proposed here, not necessarily a recommendation tested by the source.

## Foundations and standards

### 1. Mynavi TechTus Vietnam / Hai Thang — Color in UI design, Part 1 (2023)

[Article](https://medium.com/@MynaviTechTusVietnam/color-in-ui-design-part-1-foundation-of-using-color-to-create-effectively-ui-034f9da6995d). Practitioner introduction; article body reviewed.

**Takeaway:** Color can establish hierarchy, relationships, and emphasis. Scheme families provide starting directions, and audience feedback helps choose among them.

**Limit:** Its named-color examples are not consistently reliable. In particular, blue/yellow/orange does not illustrate an evenly spaced triad on a conventional wheel; the blue/yellow-green/blue-violet split-complementary example also needs correction. Hue contrast does not guarantee readable luminance contrast.

**Skill use:** Retain the composition vocabulary; define the color model and validate every resulting UI pairing. Do not encode the example palettes as rules.

### 2. W3C — WCAG 2.2 and Understanding Contrast (Minimum)

[Normative recommendation](https://www.w3.org/TR/WCAG22/) and [SC 1.4.3 explanation](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html). Standard plus informative guidance; relevant text reviewed.

**Takeaway:** Text contrast has measurable thresholds and scoped exceptions; brand identity does not exempt ordinary interface text.

**Skill use:** Use explicit text/background acceptance checks. Distinguish the normative requirement from explanatory advice, and avoid declaring a whole interface accessible from a palette test.

### 3. W3C — Understanding Non-text Contrast, SC 1.4.11

[Guidance](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html). Informative explanation of an AA criterion; relevant text reviewed.

**Takeaway:** Required control/state cues and meaningful graphics need contrast against adjacent colors. Decorative boundaries and differences between nonadjacent interaction states are not blanket 3:1 requirements.

**Skill use:** Check the visual information that makes a control or chart understandable, rather than flagging every subtle divider.

### 4. W3C — Understanding Use of Color, SC 1.4.1

[Guidance](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html). Informative explanation of a Level A criterion; relevant text reviewed.

**Takeaway:** People must be able to obtain meaning conveyed through color without identifying the hue. Programmatic labels alone do not supply the visible alternative needed by sighted users who cannot distinguish the colors.

**Skill use:** Add visible labels, symbols, patterns, or other appropriate cues to status, validation, selection, and data.

### 5. W3C — Understanding Focus Appearance, SC 2.4.13

[Guidance](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance) and [normative criterion](https://www.w3.org/TR/WCAG22/#focus-appearance). AAA criterion; relevant text reviewed.

**Takeaway:** Focus indicator area and contrast change have a defined enhanced target. This is distinct from AA focus visibility and non-text contrast requirements.

**Skill use:** Make focus intentional and testable; do not mislabel the AAA area requirement as AA.

## Design systems and implementation sources

### 6. Google — Material Design 3 in Compose

[Official implementation guide](https://developer.android.com/develop/ui/compose/designsystems/material3). Platform guidance; color sections reviewed.

**Takeaway:** Color schemes assign roles and paired “on” colors; light, dark, and dynamic schemes can populate the same interface structure.

**Skill use:** Map Android components to `MaterialTheme.colorScheme` and preserve intended foreground/container pairings. Consider dynamic color with the product's branding requirements and supported OS versions.

**Access:** The Material 3 color-role website returned a JavaScript shell. Google's substantive Android documentation supplies the evidence here.

### 7. Apple — Color and Dark Mode

[Color](https://developer.apple.com/design/human-interface-guidelines/color) and [Dark Mode](https://developer.apple.com/design/human-interface-guidelines/dark-mode). Platform guidance; Color's official Markdown body and indexed Dark Mode guidance reviewed.

**Takeaway:** Semantic colors adapt to environment and appearance; custom assets need appropriate variants. Backgrounds and translucent materials affect color perception and legibility.

**Skill use:** Use semantic platform colors for their intended roles, and named adaptive assets for custom colors. Check light/dark and increased contrast with the actual material and content behind controls. Do not copy published system RGB values into permanent app constants.

### 8. IBM — Carbon Color

[Official guidance](https://www.carbondesignsystem.com/building-blocks/foundations/color/overview). Design-system practice; page reviewed; updated September 25, 2026.

**Takeaway:** Tokens describe stable roles; themes supply values. Layering and interaction states are explicit parts of the system.

**Skill use:** Separate primitive values, semantic roles, and component bindings. Specify surface hierarchy and state mappings. Carbon's exact palette and layering rules are implementation choices, not universal design laws.

### 9. Radix — Understanding the Scale

[Official guidance](https://www.radix-ui.com/colors/docs/palette-composition/understanding-the-scale). Practitioner implementation reference; page reviewed.

**Takeaway:** A useful ramp has colors for specific jobs—surfaces, states, borders, fills, and text. Some bright solid colors require dark foregrounds.

**Limit:** Documented guarantees are specific to pairings and metrics; the page discusses APCA for certain text pairs.

**Skill use:** Borrow role-aware ramp construction. Measure the actual combination with the project's required contrast metric instead of assuming every scale step is interchangeable or WCAG 2.2 compliant.

### 10. Björn Ottosson — A Perceptual Color Space for Image Processing (2020; introduction updated 2025)

[Author's technical article](https://bottosson.github.io/posts/oklab/). Original model explanation, not a UI outcome experiment; technical description reviewed.

**Takeaway:** Oklab aims to separate perceptual lightness, chroma, and hue more usefully than conventional RGB-derived manipulations for operations such as interpolation.

**Skill use:** Use perceptual coordinates to create and tune ramps, then inspect rendered results. Treat uniformity as an approximation, not proof of equal usability or readability.

### 11. W3C — CSS Color Module Level 4

[Specification](https://www.w3.org/TR/css-color-4/). Technical specification; inspected October 8, 2026 Candidate Recommendation Draft, including Oklab/OKLCH sections.

**Takeaway:** CSS defines perceptual color syntax, color spaces, and gamut handling. A valid color coordinate need not be reproducible on every display.

**Skill use:** Keep the authoring model distinct from delivery gamut and supported syntax. Check browser targets and converted/rendered values; do not equate OKLCH lightness with WCAG relative luminance.

### 12. W3C — CSS Color Adjustment Module Level 1

[Specification](https://www.w3.org/TR/css-color-adjust-1/). Candidate Recommendation Snapshot dated December 16, 2025; relevant sections reviewed.

**Takeaway:** Browsers can adapt native UI and author colors to appearance preferences or forced palettes. Opting out prevents those adaptations.

**Skill use:** Coordinate `color-scheme` with the actual theme and test forced-colors behavior. Avoid global opt-outs that override a user's chosen palette.

### 13. Cynthia Brewer / ColorBrewer — Color Scheme Types

[Project guidance](https://colorbrewer2.org/learnmore/schemes_full.html). Visualization design guidance; page reviewed.

**Takeaway:** Sequential scales express order; diverging scales emphasize a meaningful center; qualitative palettes distinguish categories without imposing magnitude.

**Skill use:** Choose the encoding from the data type and task before selecting hues. The same scheme is not suitable for categories, temperatures, and deviations from a target.

## Research papers

### 14. Jonauskaite et al. — Universal Patterns in Color–Emotion Associations Are Further Shaped by Linguistic and Geographic Proximity (2020)

[Journal abstract](https://www.psychologicalscience.org/journals/psychological-science/0956797620948810/) · DOI: `10.1177/0956797620948810`. Psychological Science. Peer-reviewed cross-national research; abstract reviewed, not full methods.

**Finding:** Among 4,598 participants in 30 nations, color-term/emotion associations shared substantial patterns while also varying with linguistic and geographic proximity.

**Limit:** This measured associations with color terms, not whether a colored button causes emotion, trust, or purchase behavior.

**Skill use:** Treat emotional direction as a culturally informed hypothesis. Validate important status meanings and brand interpretations with the intended audience.

### 15. Skulmowski et al. — The Negative Impact of Saturation on Website Trustworthiness and Appeal (2016)

[Publisher page](https://www.sciencedirect.com/science/article/pii/S0747563216302254) · DOI: `10.1016/j.chb.2016.03.054`. Computers in Human Behavior. Peer-reviewed experiment; indexed publisher abstract/highlights reviewed; direct page retrieval returned 403.

**Finding:** Ratings of saturated/desaturated versions of 50 sites across 10 content domains showed domain-dependent negative effects of higher saturation. Exposure duration was also varied.

**Limit:** These were judgments of appearance, trustworthiness, and perceived usability; they do not establish actual task performance or conversion, nor that all saturated interfaces are poor.

**Skill use:** Tune saturation to content and desired emphasis; compare alternatives in representative screens instead of maximizing intensity by default.

### 16. Buchner and Baumgartner — Text–Background Polarity Affects Performance Irrespective of Ambient Illumination and Colour Contrast (2007)

[Publisher abstract](https://www.tandfonline.com/doi/abs/10.1080/00140130701306413) · [PubMed record](https://pubmed.ncbi.nlm.nih.gov/17510822/) · DOI: `10.1080/00140130701306413`. Ergonomics. Peer-reviewed experiments; abstract reviewed, not full methods.

**Finding:** Proofreading favored dark text on light backgrounds in the tested conditions; hue differences could not compensate for insufficient luminance contrast. Reported strain and physiological measures did not differ with the manipulated conditions.

**Limit:** This task and study population do not settle preferences, all visual impairments, modern device contexts, or long-term health effects.

**Skill use:** Keep reading performance separate from appearance preference. Test the relevant task and preserve user choice rather than claiming that dark mode universally reduces strain.

### 17. Danielle Albers Szafir — Modeling Color Difference for Visualization Design (2018)

[Author-hosted manuscript](https://danielleszafir.com/colordiff_vis2017.pdf) · [Publication record](https://pubmed.ncbi.nlm.nih.gov/28866544/) · DOI: `10.1109/TVCG.2017.2744359`. IEEE TVCG 24(1), 392–401. Peer-reviewed experiments; manuscript abstract, introduction, and study framing reviewed. Conference-era manuscript is dated 2017; journal publication is 2018.

**Finding:** Color discrimination varies with the size and shape of visualization marks; isolated large swatches do not capture all relevant behavior.

**Limit:** The experiments studied specific mark comparisons and conditions, not universal palette guarantees.

**Skill use:** Evaluate color differences in the actual points, bars, and lines at realistic sizes. Do not assume a fixed color-distance cutoff makes every chart readable.

### 18. Crameri, Shephard, and Heron — The Misuse of Colour in Science Communication (2020)

[Open-access paper](https://www.nature.com/articles/s41467-020-19160-7) · DOI: `10.1038/s41467-020-19160-7`. Nature Communications 11, 5444. Peer-reviewed methodological synthesis and demonstrations; relevant color-map discussion reviewed.

**Takeaway:** Uneven color maps can hide variation or introduce apparent boundaries; perceptual order, color-vision accessibility, and the appropriate map class matter.

**Limit:** This concerns data representation, not a rule against expressive colors in product branding.

**Skill use:** Prefer ordered, perceptually considered scales for continuous data; avoid rainbow defaults, retain legends, and inspect the scale against its actual background.

## How the sources combine

The proposed workflow connects complementary evidence:

1. **Intent and composition:** Use source 1 for vocabulary, with sources 14–16 constraining claims about emotion, intensity, and appearance preference.
2. **Color architecture:** Use sources 6–9 for reusable roles, paired foregrounds, and state/theme mappings.
3. **Palette construction:** Use sources 10–11 for perceptual authoring and delivery constraints.
4. **Acceptance checks:** Use sources 2–5 for measurable color-related criteria and source 12 for browser adaptation.
5. **Data encoding:** Use sources 13, 17, and 18 for scale selection and validation in actual charts.

This synthesis supports three outputs: a design with rationale, an implemented theme/component change, or a review with measured findings. None of these sources justifies a universal “best color,” an automatic conversion uplift, or an accessibility claim based only on harmonious swatches.
