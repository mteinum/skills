# Creative assets and In-App Events

Read for product page headers, search artwork, universal artwork, and event cards/detail media. Use current Apple templates and specifications for the actual output, not a screenshot export preset.

## Headers and search artwork

[Apple's asset guidance](https://developer.apple.com/app-store/asset-best-practices/) recommends a focused header and an obvious purpose in search artwork. Use its linked design templates and inspect their safe areas for each placement.

According to [Manage your App Store assets](https://developer.apple.com/help/app-store-connect/manage-app-information/manage-your-app-store-assets), creative assets are optional and distinct from screenshots, previews, purchase/subscription images, and artwork specifically requested by Apple's editorial team. Verify OS and placement availability before promising where artwork will appear. In Asset Library, inspect compatibility and usage before reusing an asset. Poster-frame changes can affect every use of an asset, and approved poster frames cannot be edited.

Use [Creative assets specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/creative-assets-specifications) to resolve dedicated versus universal exports. The researched image options include:

| Placement | Dedicated image | Universal image |
| --- | --- | --- |
| Header | 3840 × 1646; 21:9 | 5244 × 2950 PNG; 16:9 |
| Search | 1920 × 1280 to 3840 × 2560; 3:2 | 5244 × 2950 PNG; 16:9 |

Dedicated images accept JPEG/JPG/PNG; images cannot contain alpha or transparency. Header/search videos use their dedicated placement resolutions, 30 or 60 fps, 5–30 seconds, and MOV/M4V/MP4. Search video is silent with no unmute control; product-page video starts muted but supports unmuting. These values are a dated orientation aid, not an exhaustive encoding specification. Refresh them before production; universal image support does not establish universal video support.

## Event media

Consult [In-App Events](https://developer.apple.com/app-store/in-app-events/) for event eligibility and metadata. Establish the actual limited-time experience and suitable badge before making artwork. General awareness campaigns, repetitive daily rewards, and price-only promotions are unsuitable event concepts.

Make media specific to the event. Prefer artwork without embedded names or logos where the surrounding metadata already supplies them. Avoid baked-in borders or gradients; the store applies its own presentation treatments. Keep card and detail artwork visually related and preview both with surrounding text and badges.

The [creative specification](https://developer.apple.com/help/app-store-connect/reference/app-information/creative-assets-specifications) requires landscape 16:9 card media and portrait 9:16 detail media. Follow its linked In-App Event media specification for resolution ranges, image limits, video encoding, and audio. Compose both versions deliberately rather than stretching one into the other.

For handoff, associate each export with its card/detail placement, locale, event reference, and intended poster frame. If publishing is in scope, verify the event metadata and timing separately from visual approval.
