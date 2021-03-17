Pattern: Unnecessary `!!`

Issue: -

## Description

Reports unnecessary not-null operator usage (`!!`) that can be removed by the user.
Example of **incorrect** code:

```kotlin
val b = a!!

Example of **correct** code:

```kotlin
val b = a

## Further Reading

* [Detekt - UnnecessaryNotNullOperator](https://arturbosch.github.io/detekt/potential-bugs.html#unnecessarynotnulloperator)