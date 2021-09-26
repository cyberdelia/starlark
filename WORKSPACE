load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

BAZEL_TAG = "4.2.1"
BAZEL_SHA = "aab6f2148cd0888a3ae797e49745c18161cac2940c3be26bf5901d35e1f8760b"

http_archive(
    name = "bazel",
    url = "https://github.com/bazelbuild/bazel/archive/%s.zip" % BAZEL_TAG,
    sha256 = BAZEL_SHA,
    strip_prefix = "bazel-" + BAZEL_TAG,
    patches = ["//:0001-fix-invalid-javadoc.patch"],
    patch_args = ["-p1"]
)

BAZEL_SKYLIB_TAG = "1.0.3"
BAZEL_SKYLIB_SHA = "1c531376ac7e5a180e0237938a2536de0c54d93f5c278634818e0efc952dd56c"

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

RULES_PKG_TAG = "0.5.1"
RULES_PKG_SHA = "a89e203d3cf264e564fcb96b6e06dd70bc0557356eb48400ce4b5d97c2c3720d"

http_archive(
    name = "rules_pkg",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/%s/rules_pkg-%s.tar.gz" % (RULES_PKG_TAG, RULES_PKG_TAG),
        "https://github.com/bazelbuild/rules_pkg/releases/download/%s/rules_pkg-%s.tar.gz" % (RULES_PKG_TAG, RULES_PKG_TAG),
    ],
    sha256 = RULES_PKG_SHA,
)
load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")
