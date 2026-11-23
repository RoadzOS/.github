# Contributing to RoadzOS

Thank you for helping build RoadzOS. These rules apply to every repository in the organisation unless a repository's own `CONTRIBUTING.md` says otherwise.

## Where a change belongs

| Change | Repository |
|---|---|
| A catalogue entry, pictogram, colour, token, severity rule or composition layout | [roados-visual-hazard-studio](https://github.com/RoadzOS/roados-visual-hazard-studio): the source of truth for RVHL |
| Rendering, SVG support, the C++ API, RVHL loading or composition in native code | [roados-graphics-core](https://github.com/RoadzOS/roados-graphics-core) |
| Swift, SwiftUI or UIKit API, or the iOS sample | [roados-ios-sdk](https://github.com/RoadzOS/roados-ios-sdk) |
| Kotlin, Compose or Android View API, or the Android sample | [roados-android-sdk](https://github.com/RoadzOS/roados-android-sdk) |

## Ground rules

1. **One renderer.** Never add drawing or composition logic in Swift or Kotlin. Add it to the core (`roados::binding` if the SDKs need it), and keep the bridges to marshalling only.
2. **Never hand-edit generated RVHL assets.** `assets/rvhl/` and `tests/fixtures/rvhl-golden/` in the core are generated from a pinned Studio commit by `scripts/export_rvhl.sh` (and `--golden`). Change the Studio, then bump the pin.
3. **Never invent or rename catalogue identifiers.** Element IDs (`RDM-003`) are the stable keys.
4. **Test what you change** and report the results you actually observed. If you couldn't build or run something, say so in the pull request.
5. **Pin dependencies.** Skia, the Studio and the core are pinned by commit. Update them in a separate, reviewed change.

## Pull requests

* Keep each pull request focused on one change, and explain *why* in the description.
* Include the test commands you ran and their results:
  * core: `ctest --preset macos-debug`;
  * iOS: `swift test`, or `xcodebuild test` on a simulator;
  * Android: `scripts/host_jni_test.sh` and `./gradlew check`.
* Visual changes should include before and after images.

## Licensing

No licence has been chosen for the RoadzOS repositories yet. Until one is published, ask the maintainers before you reuse code or assets outside RoadzOS.
