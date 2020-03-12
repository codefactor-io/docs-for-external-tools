Pattern: Forbidden public data class

Issue: -

## Description

The data classes are bad for the binary compatibility in public APIs. Avoid to use it.
This rule is aimed to library maintainers. If you are developing a final application you don't need to care about this issue.
Example of **incorrect** code:

```kotlin

Example of **correct** code:

```kotlin
## Further Reading

* [Detekt - ForbiddenPublicDataClass](https://arturbosch.github.io/detekt/style.html#forbiddenpublicdataclass)