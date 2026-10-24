# Review and validation

This is the skill's review method, not an official Apple scoring or certification scheme. Apply it to the requested scope.

## Match claims to evidence

| Evidence available | What it can support | What remains to verify |
| --- | --- | --- |
| Screenshot or static design | Visible hierarchy, labels, apparent grouping, and presentation choices. | Actual hit areas, accessibility semantics, focus routes, dismissal, animations, and other states. |
| Source code | Component choice, state handling, explicit constraints, API use, and declared semantics. | The composed interface and interaction on the target platform. |
| Running app or simulator | Reproduced flows, transitions, alternate settings, and input that the environment supports. | Hardware-specific behavior or comfort not represented by the environment. |
| Physical device | Behavior tested under the recorded device and settings. | Other platforms, devices, settings, and untested flows. |

A screenshot's pixel dimensions do not establish point sizes without a reliable scale. Apparent contrast in compressed media is not a measured contrast ratio. Label estimates and untested behavior explicitly.

## Inspect the real flow

Start from the user's task, such as finding an item, editing it, and saving or cancelling. Inspect the states that affect that task: initial, populated, empty, loading, failure, disabled, and recovery where applicable.

Record the scope, platform, OS, evidence, and relevant constraints. Follow the source links in [Patterns and foundations](patterns-and-foundations.md) for the specific decision. Do not present preference alone as a violation.

Use priorities based on user impact:

- **High:** the evidence shows a blocked essential task, inaccessible essential action, or a credible path to unintended data loss.
- **Medium:** a repeated navigation, readability, feedback, or recovery problem substantially impairs the task.
- **Low:** a supported polish or consistency issue with limited impact on task completion.

These labels describe this review's impact assessment. They are not Apple's severity levels, and a hypothetical failure needs verification before being labeled a demonstrated blocker.

## Write actionable findings

For each supported finding, provide:

1. **Location and condition:** screen/component and the state or steps that expose it.
2. **Observation and impact:** what the evidence shows and how it affects the person.
3. **Basis:** the relevant Apple page and platform qualification, or an explicitly labeled design judgment.
4. **Remedy and verification:** a concrete change and how to check that it solves the problem.

For code, include the relevant file and line when available. For designs, identify the frame or element. A useful finding connects evidence to a remedy; a generic checklist without observed problems is not a completed review.

List uncertain concerns separately as checks to perform. If no actionable findings are supported, report that and the limits of the evidence rather than claiming universal compliance.

## Verify changes proportionately

For design-only work, inspect the relevant alternate layouts and states, and document behavior the artifact cannot demonstrate. For code changes, build the affected target and exercise the modified flow.

Choose from these checks based on what changed:

| Change | Verification |
| --- | --- |
| Navigation or presentation | Reach the task, navigate back, dismiss/cancel, preserve selection, and handle unsaved work. |
| Layout or typography | Relevant window sizes, text-size settings, keyboard presentation, and representative long or RTL text. |
| Colors or materials | Supported appearance modes, increased contrast/reduced transparency where available, and changing content backgrounds. |
| Controls or input | Accessible names and state, focus traversal, keyboard/pointer/touch/remote paths appropriate to the platform. |
| Animation or transitions | Reduced motion, interruption, state continuity, and immediate access to essential actions. |
| Error or permission flow | Failure, denial, retry, cancellation, and continued access to unaffected tasks. |

Use existing previews, UI tests, and accessibility tools where useful. Add regression tests when they protect behavior affected by the change, not simply to assert chosen padding or copy.

Report what was actually checked and what still needs runtime or device verification. HIG alignment does not prove App Store approval or complete accessibility coverage.
