load("@rules_jvm_external//:defs.bzl", "java_export")

java_export(
  name = "starlark",
  maven_coordinates = "com.lapanthere:starlark:5.3.2.1",
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
