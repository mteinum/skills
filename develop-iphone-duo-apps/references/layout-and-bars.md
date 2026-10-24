# Layout and bars

Checked against Apple documentation on 2026-10-24. Treat the following availability values as a verified starting point; check the selected SDK and each symbol before use.

## Availability map

| Capability | SwiftUI | UIKit | Documented iOS introduction |
| --- | --- | --- | --- |
| Two related content surfaces | [ArrangementView](https://developer.apple.com/documentation/swiftui/arrangementview) | [UIArrangementViewController](https://developer.apple.com/documentation/uikit/uiarrangementviewcontroller) | 27.1 for both |
| Reserved-region query | [GeometryProxy.reservedRegions](https://developer.apple.com/documentation/swiftui/geometryproxy/reservedregions(kind:options:layoutdirectionbehavior:)) | [UIView.reservedRegions](https://developer.apple.com/documentation/uikit/uiview/reservedregions(kind:options:)) | 27.1 for both |
| Preferred vertical bar edge | [toolbarVerticalEdge](https://developer.apple.com/documentation/swiftui/environmentvalues/toolbarverticaledge) | [verticalBarEdge](https://developer.apple.com/documentation/uikit/uitraitcollection/verticalbaredge) | 27.1 for both |
| Toolbar axis eligibility | [ToolbarContent.axisBehavior](https://developer.apple.com/documentation/swiftui/toolbarcontent/axisbehavior(_:)) | UIBarButtonItem.axisBehavior | 27.1 verified for SwiftUI; check UIKit |
| Overflow priority | [ToolbarContent.visibilityPriority](https://developer.apple.com/documentation/swiftui/toolbarcontent/visibilitypriority(_:)) | UIBarButtonItem.visibilityPriority | 27.0 verified for SwiftUI; check UIKit |
| Pin a prominent trailing action | [topBarPinnedTrailing](https://developer.apple.com/documentation/swiftui/toolbaritemplacement/topbarpinnedtrailing) | UINavigationItem.pinnedTrailingGroup | 27.0 verified for SwiftUI; check UIKit |

Do not assign one release requirement to every Duo-related symbol. Check other platform availabilities separately for shared targets.

## Choose a container

A navigation split view expresses information hierarchy and selection. An arrangement view lays out two related surfaces and does not replace navigation.

- A split arrangement separates primary and secondary content along an allowed axis.
- An overlay arrangement puts primary content above secondary content on a flat display. When divided by a fold, primary content occupies the trailing or bottom region; secondary content occupies the leading or top region.
- Axis restrictions can suppress a secondary surface in some configurations. Test how users reach its actions when it is absent.

These behaviors and the `arrangementViewStyle` configuration are documented in [ArrangementView](https://developer.apple.com/documentation/swiftui/arrangementview). UIKit uses `setViewController(_:for:)` and `updateArrangement(_:animated:)`; see [UIArrangementViewController](https://developer.apple.com/documentation/uikit/uiarrangementviewcontroller).

Keep navigation outside the arrangement's content. Apple's HIG describes navigation containers around arrangements, while the symbol documentation cautions against embedding arrangements in split views, scrolling containers, and grids. For implementation, follow the specific container's documentation: do not mechanically wrap a list cell or split-view detail in an arrangement. Choose the appropriate outer layout owner and verify every surface remains reachable. This is a conservative interpretation of the [HIG](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo) and [ArrangementView constraints](https://developer.apple.com/documentation/swiftui/arrangementview), not a requirement to replace existing navigation.

## Reserved regions in custom layouts

Distinguish `.occlusion`, where hardware covers content, from `.division`, where content needs separate usable areas. Safe-area insets alone do not describe an interior fold.

Query the view that actually positions the content. Both frameworks return overlapping regions in that view's coordinates, including partial overlaps. Frames may extend beyond the view, and already include the supplied margins; do not add those margins again. Default queries include active regions. Only request `.includeInactive` when deliberately reserving space in advance, and account for `isActive`.

The outer camera region remains active; the inner camera's region depends on camera use; a fold division becomes inactive when fully open. Lists and other scrolling containers do not automatically divide rows around a fold. Inspect custom controls and spanning rows even when surrounding navigation adapts correctly. See [SwiftUI ReservedRegion](https://developer.apple.com/documentation/swiftui/reservedregion) and [UIKit UIView.ReservedRegion](https://developer.apple.com/documentation/uikit/uiview/reservedregion).

### SwiftUI coordinate handling

Use `GeometryReader` and `GeometryProxy.reservedRegions(kind:options:layoutDirectionBehavior:)`. For a custom `Layout`, calculate in the queried view's local coordinates and account for `bounds.origin` at placement. SwiftUI mirrors returned frames by default for layouts that mirror in right-to-left languages. Request `.fixed` only when your placement does not mirror. Avoid a second manual mirror.

These are the query's documented [coordinate and layout-direction semantics](https://developer.apple.com/documentation/swiftui/geometryproxy/reservedregions(kind:options:layoutdirectionbehavior:)). As an implementation check, intersect returned regions with the actual usable bounds before deriving sizes, so partial overlaps cannot produce negative pane dimensions.

### UIKit update handling

Use Auto Layout and query `reservedRegions(kind:options:)` in `updateConstraints()` for constraint-driven geometry. UIKit tracks those reads and reevaluates when the regions change; a one-time query in `viewDidLoad` is insufficient. See [UIView.reservedRegions](https://developer.apple.com/documentation/uikit/uiview/reservedregions(kind:options:)).

## System bars and overflow

Attach SwiftUI toolbars to navigation containers. In UIKit, configure a view controller inside a navigation controller instead of assembling standalone bar views. Supply a title and icon for adaptable actions: text-only items and custom-view items do not appear vertically. Use semantic placements and related groups.

Inspectors retain horizontal bars; multi-column split views treat sidebar/content bars differently from detail bars. Sheets vary with display and placement. For a diagnosed sheet issue, inspect `toolbarVerticalBehavior(_:)` / `preferredVerticalBarBehavior` and `presentationPlacement(_:)` / `preferredPlacement`; avoid disabling vertical presentation app-wide.

For dedicated overflow entries, inspect `ToolbarOverflowMenu` or `UINavigationItem.additionalOverflowItems`. The engineering overview documents these [bar integration and item rules](https://developer.apple.com/documentation/technologyoverviews/preparing-your-app-for-iphone-duo).

### Read placement rather than guessing

`toolbarVerticalEdge` and `verticalBarEdge` indicate the system's preferred edge even when a bar is hidden. SwiftUI returns `nil` and UIKit reports an unspecified edge when vertical placement does not apply. Do not use these values as visibility flags. See [SwiftUI edge semantics](https://developer.apple.com/documentation/swiftui/environmentvalues/toolbarverticaledge) and [UIKit edge semantics](https://developer.apple.com/documentation/uikit/uitraitcollection/verticalbaredge).

Respect asymmetric safe areas: a multitasking app can put controls on either outer edge. Content can mirror for RTL while hardware-aligned controls retain their physical side. Follow system placement instead of hard-coding trailing/right. See [vertical controls](https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo#Vertical-controls).

### Prioritize actions deliberately

Lower `visibilityPriority` values send items into overflow sooner; prioritize the actions or status indicators the task needs most. [Visibility priority documentation](https://developer.apple.com/documentation/swiftui/toolbarcontent/visibilitypriority(_:)) describes this ordering.

`axisBehavior` controls which bar axes can host an item; restricting an item to horizontal bars is not an overflow-priority setting. Ensure an alternative route to any action excluded from a visible axis. See [axis behavior](https://developer.apple.com/documentation/swiftui/toolbarcontent/axisbehavior(_:)).

`topBarPinnedTrailing` suits prominent actions, but pinned items can still overflow while search is active and space is insufficient. Test that combination. See [pinned trailing placement](https://developer.apple.com/documentation/swiftui/toolbaritemplacement/topbarpinnedtrailing).
