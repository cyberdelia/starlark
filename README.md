# Starlark

This provides [Starlark](https://github.com/bazelbuild/starlark#overview) as a standalone java library, distinct
from [Bazel](https://github.com/bazelbuild/bazel). There is
no [API stability guarantee](https://github.com/bazelbuild/bazel/issues/2367#issuecomment-778694264), so do exercise
caution if you decide to use this library.

## Installation

This library is published to Treasure Data internal maven repository, you can add it in your project fairly easily.

### Using Gradle

```kotlin
repositories {
    maven {
        url = uri("https://treasuredata.jfrog.io/treasuredata/libs-release")
        credentials {
            username = System.getenv("TD_JFROG_USERNAME") 
            password = System.getenv("TD_JFROG_PASSWORD")
        }
    }
}

dependencies {
    implementation("com.treasuredata:starlark:4.2.1")
}
```

## Usage

To embed and use the interpreter in your program:

### Java

```java
StarlarkSemantics semantics = StarlarkSemantics.DEFAULT;
try (Mutability mu = Mutability.create("scope")) {
    StarlarkThread thread = new StarlarkThread(mu, semantics);
    Module module = Module.withPredeclared(semantics, new HashMap<>());
    Program program = Program.compileExpr(Expression.parse(ParserInput.fromLines("print('hello')")), module, FileOptions.DEFAULT);
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
        Program.compileExpr(Expression.parse(ParserInput.fromLines("""print("hello")""")), module, FileOptions.DEFAULT)
    Starlark.execFileProgram(program, module, thread)
}
```
