Pattern: Use of truthy/falsy matcher

Issue: -

## Description

Truthy/falsy matchers coerce values to boolean and can hide type mistakes. Strict boolean assertions make intent explicit and avoid accidental coercion.

## Examples

Example of **incorrect** code:

```ts
expect(foo).toBeTruthy();
expectTypeOf(foo).toBeTruthy();
expect(foo).toBeFalsy();
expectTypeOf(foo).toBeFalsy();
```

Example of **correct** code:

```ts
expect(foo).toBe(true);
expectTypeOf(foo).toBe(true);
expect(foo).toBe(false);
expectTypeOf(foo).toBe(false);
```