load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")
load("@build_bazel_rules_apple//apple:macos.bzl", "macos_application")
load("@build_bazel_rules_apple//apple:versioning.bzl", "apple_bundle_version")
load("@build_bazel_rules_apple//apple:apple.bzl", "apple_dynamic_xcframework_import")

apple_bundle_version(
    name = "FuwariVersion",
    build_version = "0.6.0",
)

swift_library(
    name = "FuwariLib",
    srcs = glob([
        "Fuwari/*.swift",
    ]),
)

macos_application(
    name = "macos-app",
    bundle_id = "com.appknop.fuwari",
    infoplists = [":Fuwari/Info.plist"],
    minimum_os_version = "10.13",
    version = ":FuwariVersion",
    deps = [":FuwariLib"],
)

apple_dynamic_xcframework_import(
    name = "ThirdPartySDK",
    xcframework_imports = glob(["Carthage/Build/**"]),
)
