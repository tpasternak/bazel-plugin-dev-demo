workspace(name = "demo_plugin")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:jvm.bzl", "jvm_maven_import_external")

http_archive(
    name = "rules_intellij",
    patch_args = ["-p1"],
    #    path = "/home/t/repos/intellij-bazel",
    patches = [
        "//:rules_intellij.patch",
        "//:patch2.patch",
        "//:patch3.patch",
    ],
    sha256 = "d88df86a913eb586f11530a5a5ee378744d9d29d5cfa7a27b456d2f036fd8f52",
    strip_prefix = "intellij-2023.05.16-rc-1",
    url = "https://github.com/bazelbuild/intellij/archive/refs/tags/v2023.05.16-rc-1.zip",
)

# The plugin api for intellij_ce_2023_1. This is required to build IJwB and run integration tests.
IC_231_SHA = "d693dd44a900341d1362f105fea1adc79f0e04bc6f52f783883e75bf88f76793"

IC_231_URL = "https://www.jetbrains.com/intellij-repository/releases/com/jetbrains/intellij/idea/ideaIC/231.8109.175/ideaIC-231.8109.175.zip"

http_archive(
    name = "intellij_ce_2023_1",
    build_file = "@rules_intellij//intellij_platform_sdk:BUILD.idea231",
    sha256 = IC_231_SHA,
    url = IC_231_URL,
)

jvm_maven_import_external(
    name = "auto_value_annotations",
    artifact = "com.google.auto.value:auto-value-annotations:1.6.2",
    artifact_sha256 = "b48b04ddba40e8ac33bf036f06fc43995fc5084bd94bdaace807ce27d3bea3fb",
    licenses = ["notice"],  # Apache 2.0
    server_urls = ["https://repo1.maven.org/maven2"],
)

jvm_maven_import_external(
    name = "error_prone_annotations",
    artifact = "com.google.errorprone:error_prone_annotations:2.13.1",
    artifact_sha256 = "f5ee2aac2ee6443789e1dee0f96e3c35d9f3c78891f54ed83f3cf918a1cde6d1",
    licenses = ["notice"],  # Apache 2.0
    server_urls = ["https://repo1.maven.org/maven2"],
)
