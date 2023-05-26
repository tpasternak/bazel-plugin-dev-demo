load(
    "@rules_intellij//build_defs:build_defs.bzl",
    "intellij_plugin",
    "intellij_plugin_library",
    "stamped_plugin_xml",
)
load(
    "@rules_intellij//intellij_platform_sdk:build_defs.bzl",
    "select_for_ide",
    "select_from_plugin_api_directory",
)
load(
    "@rules_intellij//build_defs:intellij_plugin_debug_target.bzl",
    "intellij_plugin_debug_target",
)

intellij_plugin_library(
    name = "plugin_library",
    optional_plugin_xmls = [],
    plugin_xmls = [":plugin.xml"],
    visibility = ["//visibility:public"],
    deps = [":plugin_lib"],
)

java_library(
    name = "plugin_lib",
    srcs = ["Main.java"],
    deps = ["@rules_intellij//intellij_platform_sdk:plugin_api"],
)

stamped_plugin_xml(
    name = "stamped_plugin_xml",
    plugin_id = "com.example.hello.world",
    plugin_name = "Hello World Plugin",
    version = "1",
)

intellij_plugin(
    name = "plugin",
    plugin_xml = ":stamped_plugin_xml",
    tags = [],
    deps = [
        ":plugin_library",
    ] + select_for_ide(
        intellij = [],
        intellij_ue = [],
    ),
)

intellij_plugin_debug_target(
    name = "ijwb_bazel_dev",
    deps = [
        ":aspect_directory",
        ":fast_build_javac",
        ":plugin_jar",
    ],
)
