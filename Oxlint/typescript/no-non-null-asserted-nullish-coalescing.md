Pattern: Non-null assertion with nullish coalescing

Issue: -

## Description

Using a non-null assertion (`!`) on the left side of a nullish coalescing operator (`??`) is contradictory. The nullish coalescing operator already handles `null` and `undefined` cases by providing a fallback value.

## Examples

Example of **incorrect** code:
```ts
foo! ?? bar;
let x: string;
x! ?? "";
```

Example of **correct** code:
```ts
foo ?? bar;
let x: string;
x ?? "";
```