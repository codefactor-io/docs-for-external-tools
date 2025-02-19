Pattern: Type assertion of literal values

Issue: -

## Description

When working with literal values, using `as const` is preferred over explicit type assertions with literal types. The `as const` assertion lets TypeScript infer the literal type automatically without repeating the value.

## Examples

Example of **incorrect** code:
```ts
let bar: 2 = 2;
let foo = { bar: "baz" as "baz" };
const config = { name: "config" as "config" };
```

Example of **correct** code:
```ts
let bar = 2 as const;
let foo = { bar: "baz" as const };
const config = { name: "config" } as const;
```