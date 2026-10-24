# Validate iPhone Duo behavior

Use a real user flow as the test: for example, open an item, edit a field, scroll its content, present a sheet, then change pose without restarting the app. The following matrix is this skill's recommended regression coverage; apply the rows relevant to the change.

## Establish available tooling

Discover the repository's project/workspace, shared scheme, build instructions, and selected toolchain. Useful discovery commands include:

```sh
xcodebuild -version
xcodebuild -showsdks
xcrun simctl list devices available
```

Use `xcodebuild -list` and `-showdestinations` with the actual project/workspace and scheme. Choose a returned destination identifier for builds or tests rather than inventing a Duo simulator name or UDID. Use the repository's normal checks and record what was run.

A runtime `#available` fallback still requires an SDK that declares the guarded symbols. If the SDK or Duo runtime is missing, make the supported resizing changes, identify the toolchain gap, and leave pose validation explicitly unverified.

## Exercise transitions in Device Hub

Apple's [Device Hub interaction guide](https://developer.apple.com/documentation/xcode/interacting-with-your-app-in-device-hub) provides Closed, Partially Open, and Open pose buttons. Option-drag the slider below the bezel to explore intermediate fold angles. Rotate in each relevant pose. Consult the installed tool's help before automating pose changes; do not assume a `simctl fold` command exists.

The same guide notes that interacting with a physical device through Device Hub can prevent camera or microphone access. Test capture directly on the physical device with that interaction stopped.

## Coverage matrix

| Configuration or transition | Evidence to collect |
| --- | --- |
| Closed outer display | Main task and secondary actions remain reachable; content clears the camera and side bars. |
| Fully open inner display, both supported orientations | Additional context fits; navigation selection remains correct; content is not merely stretched. |
| Partially folded like a book and like a laptop | Important controls and readable units avoid divisions along both axes; pane sizes remain valid. |
| Continuous open-close-open and intermediate folds | Drafts, selection, focus, scroll position, playback, and pending work survive; no duplicate task starts. |
| Split View on either side, resizing through compact and regular widths | The app responds to its own bounds and both possible bar edges. |
| Sheets, popovers, alerts, inspectors, and context menus | Present, reposition, and dismiss correctly through transitions. |
| Crowded bars, search, and overflow | High-value actions remain available; pinned and overflow items still work. |
| Large Dynamic Type, VoiceOver, and an RTL locale | Labels fit, focus order remains useful, actions have names, and coordinate mirroring is correct. |
| Keyboard visible, background/foreground, and reduced motion where affected | Editing remains usable and state survives transition interruptions. |
| Existing supported iPhone/iPad targets and older-OS fallback | The change introduces no regression and has no unguarded unavailable symbols. |
| Camera active/inactive, if used | Layout responds to camera occlusion; preview direction, mirroring, rotation, and recording remain correct. |
| Camera accessory available/unavailable/disabled, if used | Capture remains complete without the outer display; shared state stays consistent. |

Automate regression tests for state loss, coordinate calculations, or action reachability when the change warrants them. Use visual or interactive inspection for physical placement and transitions. Do not add tests that only assert the implementation's chosen constants.

## Report evidence precisely

Record the build/test command and outcome, SDK/runtime, device, flows, and transitions actually exercised. Include before/after evidence for visual fixes when available. Separate these results:

- Compiled successfully.
- Verified interactively on a Duo simulator.
- Verified on a physical Duo.
- Still needs a specific toolchain, runtime, or hardware check.

Apple distinguishes simulator checks from hardware-dependent validation in [Device Hub](https://developer.apple.com/documentation/xcode/device-hub); camera accessories specifically require [device testing](https://developer.apple.com/documentation/avfoundation/registering-a-camera-capture-accessory-on-iphone-duo#Test-your-accessory-content-on-device).
