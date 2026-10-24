# Choose the platform context

Use the row for the actual target and read its linked Apple overview. These brief starting points were checked on 2026-10-24; they do not replace a component's platform-specific guidance.

| Platform and source | Design emphasis | Useful verification |
| --- | --- | --- |
| [iOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-ios) | Prioritize the mobile task, comfortable touch interaction, discoverable secondary actions, and adaptation to appearance and text-size changes. | Complete the main flow with the software keyboard visible, larger text, and the supported size classes. |
| [iPadOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-ipados) | Use space to expose useful context. Accommodate multitasking and combinations of touch, keyboard, pointer, and Pencil where relevant. | Resize during a task; compare touch and keyboard/pointer paths. Avoid assuming the app always fills the display. |
| [macOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-macos) | Support resizable windows, menu commands, keyboard shortcuts, precise pointer input, and sustained work with appropriate density. | Traverse the interface with the keyboard, inspect menus, and resize and switch windows. Preserve selection and work in progress. |
| [watchOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-watchos) | Favor brief, glanceable tasks and shallow navigation. Use Digital Crown interaction and related surfaces when they serve the task. | Try the critical action on the intended watch sizes and with larger text; test Crown behavior where applicable. |
| [tvOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-tvos) | Design for distance viewing and remote-driven focus. Keep the current selection clear as focus changes size and position. | Follow a complete focus route, including back navigation and disabled states; inspect clipping around focused elements. |
| [visionOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-visionos) | Select windows, volumes, or immersion to fit the experience. Prioritize comfort and the least immersion the task needs; account for eyes, hands, and assistive input. | Verify targeting, placement, resizing, and entry/exit from immersion. Record when comfort or interaction still needs device testing. |

The design emphasis summarizes each linked overview. The verification column is this skill's suggested way to gather evidence, not an Apple certification process.

## Shared concepts, distinct behavior

Sharing a task model does not require identical navigation, control density, presentation, or input across platforms. For example, a Mac command may belong in the menu bar and a toolbar while the equivalent iPhone action uses a contextual control. Judge the user's ability to complete the task on each target.

For layout, use available container space, safe areas, and the platform's layout mechanisms. Size classes are useful where supported; do not invent horizontal or vertical size classes for every framework. Apple's [Layout](https://developer.apple.com/design/human-interface-guidelines/layout) guidance distinguishes platform considerations.

For iPhone Duo, consult [Designing for iPhone Duo](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo) when folding, display transitions, or vertical bars are in scope. The separate `develop-iphone-duo-apps` skill can supply implementation detail if installed, but this skill does not require it.

## Match the existing project

Keep the user's chosen native or cross-platform stack unless a change is requested or necessary. For custom-rendered or web-backed controls, verify the observable interaction and accessibility behavior instead of assuming native appearance means native semantics.

Do not import a mobile convention into a desktop or spatial app solely because it appears in an iPhone example. Check platform applicability and the supported OS before proposing a new control.
