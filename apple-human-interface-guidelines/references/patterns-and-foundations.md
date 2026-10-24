# Patterns and foundations

Use only the sections relevant to the task. Links point to Apple sources checked on 2026-10-24; read their current platform-specific guidance before applying detailed rules.

## Navigation and actions

Use [tab bars](https://developer.apple.com/design/human-interface-guidelines/tab-bars) for primary destinations and [toolbars](https://developer.apple.com/design/human-interface-guidelines/toolbars) for actions. Keep destinations stable when their content is empty; explain the state within the destination. Do not turn an action such as creating an item into a navigation tab merely to make it prominent.

For a complex hierarchy, evaluate [sidebars](https://developer.apple.com/design/human-interface-guidelines/sidebars) and their disclosure behavior. Preserve a clear relationship between the selected destination and its content. Prioritize toolbar actions for constrained space and overflow instead of squeezing every control into view.

**Review prompts:** Can the person tell where they are? Can they return, switch destinations, and discover secondary actions? Does changing size preserve access to the same task?

## Presentation and recovery

Consult [sheets](https://developer.apple.com/design/human-interface-guidelines/sheets) for scoped auxiliary tasks. Evaluate a separate navigation flow or window for prolonged work. Make cancellation, completion, and unsaved work behavior explicit; avoid chains of sheets that obscure the return path.

Use [alerts](https://developer.apple.com/design/human-interface-guidelines/alerts) for consequential, actionable interruptions. Routine status belongs near the affected content. Assess reversibility before recommending confirmation: a common action that can be undone differs from an unusual irreversible action.

**Review prompts:** What happens after dismissal, interruption, failure, or retry? Can the person recover without losing unrelated work?

## Layout and text

Read [Layout](https://developer.apple.com/design/human-interface-guidelines/layout) for hierarchy, grouping, reading order, safe areas, and adaptation to available space. Read [Typography](https://developer.apple.com/design/human-interface-guidelines/typography) for legibility, text styles, and supported text-size adjustment. Use semantic text styles or an equivalent scaling strategy; custom branding still needs readable hierarchy.

Prefer reflow and useful disclosure to shrinking important text. Inspect localized strings, right-to-left presentation, and text enlargement. Distinguish content that must grow from navigation or transient decoration whose behavior may differ.

**Review prompts:** Which text carries the task? Does it remain readable and complete at the supported sizes? Can keyboard presentation or window resizing conceal the next action?

## Color and materials

Use [Color](https://developer.apple.com/design/human-interface-guidelines/color) to select consistent semantic meanings and appropriate appearance variants. Test custom colors in the appearances and contrast settings the platform supports.

[Materials](https://developer.apple.com/design/human-interface-guidelines/materials) distinguishes Liquid Glass for the functional control/navigation layer from standard materials in the content layer. Use system treatments where appropriate and custom glass sparingly; adding blur to every card is not a HIG objective. The clear glass variant is intended for suitable visually rich backgrounds, not as a universal style.

visionOS uses adaptive window glass and has no distinct Dark Mode setting; do not mechanically apply an iOS light/dark test matrix to it. Inspect foreground readability against the actual changing background and relevant transparency/contrast settings.

**Review prompts:** Does the hierarchy remain clear while content scrolls beneath controls? Is contrast measured against the rendered background rather than an assumed solid color?

## Accessibility and input

Read [Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility) for the applicable sizing, contrast, alternative-input, and assistive-technology guidance.

Check names, roles, values, states, grouping, and focus order for meaningful controls. Check text enlargement and reachable hit areas. Information must not depend only on color, sound, or a gesture. Provide an accessible route to essential actions.

Treat default sizes and minimum sizes as different concepts, and inspect spacing alongside size. Do not declare every control under 44 points noncompliant or use a published minimum as a reason to shrink a comfortable control. Verify the specific platform and context.

**Review prompts:** Can a person complete the task with VoiceOver or the relevant alternative input? Does an icon-only action have an understandable name? Can a timed message be recovered or read at the person's pace?

## Motion and feedback

Read [Motion](https://developer.apple.com/design/human-interface-guidelines/motion). Animation should explain state or spatial relationships without delaying repeated actions. Accommodate reduced motion and retain the information when animation is reduced or absent.

**Review prompts:** Can the task continue during a transition? Is completion or failure understandable without the animation? Do focus and selection survive the transition?

## Writing and privacy prompts

Use [Writing](https://developer.apple.com/design/human-interface-guidelines/writing) for clear, contextual labels and consistent terminology. Make recovery actions specific to what the person can do.

Consult [Privacy](https://developer.apple.com/design/human-interface-guidelines/privacy) when a flow requests data or device access. Ask in the context of a feature that needs access, explain the purpose, and consider denial and restricted access. A permission required for the app's core function differs from an optional feature; avoid blanket launch-time rules.

**Review prompts:** Does the person understand the consequence of the action? Is the requested access connected to the feature they just chose? What remains usable when access is denied?

For a component or technology not covered here, follow the [HIG index](https://developer.apple.com/design/human-interface-guidelines/) to the specific topic instead of extrapolating from a superficially similar control.
