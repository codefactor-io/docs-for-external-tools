Pattern: Confusing non-null assertion placement

Issue: -

## Description

Using a non-null assertion (`!`) next to equality operators (`==`, `===`) creates code that looks similar to inequality operators (`!=`, `!==`). This similarity can lead to confusion and potential bugs.

## Examples

Example of **incorrect** code:
```ts
a! == b;   // Looks like `a != b`
a! === b;  // Looks like `a !== b`
```

Example of **correct** code:
```ts
(a!) == b;
(a!) === b;
```