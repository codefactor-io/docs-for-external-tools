Pattern: Empty object type usage

Issue: -

## Description

The empty object type `{}` is a common source of confusion as it represents any non-nullish value, including primitives like numbers and strings. Use `object` for object values or `unknown` for any value including `null` and `undefined`.

## Examples

Example of **incorrect** code:
```ts
let anyObject: {};
interface AnyValueA {}
type AnyObjectB = {};
```

Example of **correct** code:
```ts
let anyObject: object;
let anyValue: unknown;
interface UserData {
  id: number;
  name: string;
}
```