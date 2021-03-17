Pattern: Unnecessary `.?`

Issue: -

## Description

Reports unnecessary safe call operators (`.?`) that can be removed by the user.

Example of **incorrect** code:

```kotlin
val b = someValue?.length
Example of **correct** code:

```kotlin
val b = someValue?.length

## Further Reading

* [Detekt - UnnecessarySafeCall](https://arturbosch.github.io/detekt/potential-bugs.html#unnecessarysafecall)