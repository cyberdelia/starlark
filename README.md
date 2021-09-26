# Starlark

This provides [Starlark](https://github.com/bazelbuild/starlark#overview) as a standalone java library, distinct
from [Bazel](https://github.com/bazelbuild/bazel). There is
no [API stability guarantee](https://github.com/bazelbuild/bazel/issues/2367#issuecomment-778694264), so do exercise
caution if you decide to use this library.

## Installation

This library is published to Github Packages, you can add it in your project fairly easily.

### Using Gradle

```kotlin
repositories {
    maven {
        url = uri("https://maven.pkg.github.com/cyberdelia/starlark")
        credentials {
            username = project.findProperty("gpr.user") as String? ?: System.getenv("GITHUB_USERNAME")
            password = project.findProperty("gpr.key") as String? ?: System.getenv("GITHUB_TOKEN")
        }
    }
}

dependencies {
    implementation("com.lapanthere:starlark:4.2.1")
}
```

You can also refer
to [Github documentation](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-gradle-registry#using-a-published-package)
for further details.

### Using Maven

```xml

<dependencies>
    <dependency>
        <groupId>com.lapanthere</groupId>
        <artifactId>starlark</artifactId>
        <version>4.2.1</version>
    </dependency>
</dependencies>
```

You can also refer
to [Github documentation](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry#installing-a-package)
for further details.

## Usage

To embed and use the interpreter in your program:

### Java

```java
StarlarkSemantics semantics = StarlarkSemantics.DEFAULT;
try (Mutability mu = Mutability.create("scope")) {
    StarlarkThread thread = new StarlarkThread(mu, semantics);
    Module module = Module.withPredeclared(semantics, new HashMap<>());
    Program program = Program.compileExpr(Expression.parse(ParserInput.fromLines("print('hello)")), module, FileOptions.DEFAULT);
    Starlark.execFileProgram(program, module, thread);
}
```

### Kotlin

```kotlin
Mutability.create("scope").use { mu ->
    val semantics = StarlarkSemantics.DEFAULT
    val thread = StarlarkThread(mu, semantics)
    val module = Module.withPredeclared(semantics, emptyMap())
    val program =
        Program.compileExpr(Expression.parse(ParserInput.fromLines("""print("hello)""")), module, FileOptions.DEFAULT)
    Starlark.execFileProgram(program, module, thread)
}
```
