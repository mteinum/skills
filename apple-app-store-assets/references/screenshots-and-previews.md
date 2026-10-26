# Screenshots and app previews

Read for product-page captures, sequencing, video storyboards, or export validation. Recheck the linked specifications before choosing export settings.

## Content and sequence

[App Review 2.3.3–2.3.4](https://developer.apple.com/app-store/review/guidelines/#accurate-metadata) distinguishes the formats: screenshots show the app in use; app previews use screen recordings of the app itself. Explanatory overlays and preview narration are allowed. Title art, splash screens, or login screens alone do not establish the in-use screenshot requirement. Preserve the Messages experience allowance for stickers and iMessage extensions when applying the content rule; separately check whether the target supports preview uploads.

[Apple's asset guidance](https://developer.apple.com/app-store/asset-best-practices/) recommends a feature-led sequence and a complete video story. Keep screenshots centered on the experience.

For each proposed frame or scene, identify the real screen or recording that supports the claim. Missing captures are production dependencies, not permission to fabricate working UI.

## Screenshot exports

Use [Screenshot specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications) to identify required device groups, accepted pixel sizes, orientation, and scaling rules. Record the applicable row rather than assuming a familiar device's native resolution will satisfy every destination.

At research time, Apple allows 1–10 screenshots per device size in JPEG/JPG/PNG, without alpha or transparency. Scaling is conditional on consistent UI across device sizes and localizations. Check platform-specific and future-dated requirements, including any SDK-dependent conditions, before treating a new display size as mandatory today.

Inspect any scaled or cropped output for changed layouts, clipped controls, and illegible copy. Confirm that the selected capture represents the intended platform and locale.

## App preview exports

Use [App preview specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/app-preview-specifications). Select the **accepted resolution** in its table, which can differ from the physical display resolution or screenshot dimensions.

The researched specification allows up to three optional previews per supported device size and language. It lists 15–30 seconds, a 500 MB maximum, and a maximum of 30 fps. H.264 permits MOV/M4V/MP4; ProRes 422 HQ uses MOV. Recheck codec, bitrate, audio tracks, orientation, and platform support for the chosen export. A mismatched aspect ratio can move the preview into the product page's “A Closer Look” section.

Record the selected poster-frame timestamp with the export. Watch the complete encoded file, including transitions and audio, and inspect the poster frame independently. Do not substitute the more permissive frame-rate or duration settings of header/search video assets for app preview settings.
