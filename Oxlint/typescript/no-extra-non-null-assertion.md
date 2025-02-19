Pattern: Multiple non-null assertions

Issue: -

## Description

The `!` non-null assertion operator in TypeScript asserts that a value's type excludes `null` and `undefined`. Using multiple assertions on the same value is redundant and adds unnecessary noise to the code.

## Examples

Example of **incorrect** code:
```ts
const foo: { bar: number } | null = null;
const bar = foo!!!.bar;
foo!!.bar;
```

Example of **correct** code:
```ts
const foo: { bar: number } | null = null;
const bar = foo!.bar;
foo!.bar;
```