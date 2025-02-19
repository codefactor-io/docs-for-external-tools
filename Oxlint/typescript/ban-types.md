Pattern: Use of problematic TypeScript types

Issue: -

## Description

Some built-in types have better alternatives or are considered harmful. For example, using `String` instead of `string` or `Object` instead of a more specific type can lead to unexpected behavior and reduced type safety.

## Examples

Example of **incorrect** code:
```typescript
let foo: String = "foo";
let bar: Boolean = true;
```

Example of **correct** code:
```typescript
let foo: string = "foo";
let bar: boolean = true;
```