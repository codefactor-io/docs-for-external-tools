Pattern: Redundant type annotation on literal initialization

Issue: -

## Description

TypeScript can infer types from literal values, making explicit type annotations unnecessary for variables or parameters initialized with numbers, strings, or booleans.

## Examples

Example of **incorrect** code:
```ts
const a: number = 5;
const b: string = "foo";
const c: boolean = true;
const fn = (a: number = 5, b: boolean = true) => {};
```

Example of **correct** code:
```ts
const a = 5;
const b = "foo";
const c = true;
const fn = (a = 5, b = true) => {};
```