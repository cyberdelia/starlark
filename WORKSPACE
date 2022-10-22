load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

BAZEL_TAG = "5.3.2"
BAZEL_SHA = "a3fc942e8d67f06767f88469f79b6f456f853a293026b4b46e7b22526b036796"

http_archive(
    name = "bazel",
    url = "https://github.com/bazelbuild/bazel/archive/%s.zip" % BAZEL_TAG,
    sha256 = BAZEL_SHA,
    strip_prefix = "bazel-" + BAZEL_TAG,
    patch_args = ["-p1"]
)

BAZEL_SKYLIB_TAG = "1.3.0"
BAZEL_SKYLIB_SHA = "74d544d96f4a5bb630d465ca8bbcfe231e3594e5aae57e1edbf17a6eb3ca2506"

http_archive(
    name = "bazel_skylib",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/%s/bazel-skylib-%s.tar.gz" % (BAZEL_SKYLIB_TAG, BAZEL_SKYLIB_TAG),
        "https://github.com/bazelbuild/bazel-skylib/releases/download/%s/bazel-skylib-%s.tar.gz" % (BAZEL_SKYLIB_TAG, BAZEL_SKYLIB_TAG)
    ],
    sha256 = BAZEL_SKYLIB_SHA,
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

RULES_JVM_EXTERNAL_TAG = "4.1"
RULES_JVM_EXTERNAL_SHA = "f36441aa876c4f6427bfb2d1f2d723b48e9d930b62662bf723ddfb8fc80f0140"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:repositories.bzl", "rules_jvm_external_deps")

rules_jvm_external_deps()

load("@rules_jvm_external//:setup.bzl", "rules_jvm_external_setup")

rules_jvm_external_setup()

RULES_PKG_TAG = "0.7.1"
RULES_PKG_SHA = "451e08a4d78988c06fa3f9306ec813b836b1d076d0f055595444ba4ff22b867f"

http_archive(
    name = "rules_pkg",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/%s/rules_pkg-%s.tar.gz" % (RULES_PKG_TAG, RULES_PKG_TAG),
        "https://github.com/bazelbuild/rules_pkg/releases/download/%s/rules_pkg-%s.tar.gz" % (RULES_PKG_TAG, RULES_PKG_TAG),
    ],
    sha256 = RULES_PKG_SHA,
)
load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")
