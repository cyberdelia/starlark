load("@rules_jvm_external//:defs.bzl", "java_export")
load("@bazel_skylib//lib:selects.bzl", "selects")

java_export(
  name = "starlark",
  maven_coordinates = "com.lapanthere:starlark:5.3.2",
  exports = [
    "@bazel//src/main/java/net/starlark/java/annot",
    "@bazel//src/main/java/net/starlark/java/lib/json",
    "@bazel//src/main/java/net/starlark/java/eval",
    "@bazel//src/main/java/net/starlark/java/syntax"
  ],
  resources = [
    "@bazel//src/main/java/net/starlark/java/eval:cpu_profiler"
  ]
)
