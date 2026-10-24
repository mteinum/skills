# Camera behavior

Read only for apps that capture media or explicitly request outer-display camera content. Confirm API availability before implementation.

## Select cameras relative to the preview

Apple's [camera-direction guide](https://developer.apple.com/documentation/avkit/choosing-a-camera-by-the-direction-it-faces) distinguishes device position from direction relative to the view:

- Existing front-camera discovery can use the virtual front camera, which follows the active display.
- For explicit physical-camera control, use `AVCaptureDeviceDirectionCoordinator` with the preview view and applicable built-in camera types. Retain the coordinator; create and handle it on the main actor.
- Pass descriptors to the actor that owns capture. Resolve devices and reconfigure there, allowing for descriptors that no longer resolve. Avoid capture-system work in the main-actor change handler.
- Mask a transitioning preview until replacement frames arrive. Determine mirroring from direction; check mirroring support and disable automatic mirroring before assigning it manually.
- Recreate the rotation coordinator when switching capture devices.

For implementation, define what happens when no matching camera is available, rapid transitions supersede pending work, or input replacement fails. Keep that recovery within the app's existing capture ownership model.

## Offer optional outer-display content

Use [Apple's camera-accessory guide](https://developer.apple.com/documentation/avfoundation/registering-a-camera-capture-accessory-on-iphone-duo) for a requested subject preview, countdown, or script:

- SwiftUI: `sceneAccessory` with `CameraCaptureAccessory`.
- UIKit: `UISceneAccessory.cameraCapture(sceneConfiguration:userInfo:)` and `registerSceneAccessory(_:)`; retain the registration.
- Scope registration to the capture interface and share its durable model.
- Let the system choose presentation. Availability and the user's enabled preference are separate.
- Keep essential controls in the main interface. Accessory content can disappear when capture, foreground state, or device configuration changes.
- Do not add an accessory scene-manifest entry or treat this as unrestricted second-screen support.

Test real capture and accessory presentation on hardware. Simulator layout previews cannot establish that these capture-dependent behaviors work.
