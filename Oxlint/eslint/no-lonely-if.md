Pattern: Lonely `if`

Issue: -

## Description

When an `if` statement is the only statement in an `else` block, it is often clearer to use an `else if` instead.

## Examples

Example of **incorrect** code:

```ts
if (condition) {
  // ...
} else {
  if (anotherCondition) {
    // ...
  }
}
```

Example of **correct** code:

```ts
if (condition) {
  // ...
} else if (anotherCondition) {
  // ...
}
```