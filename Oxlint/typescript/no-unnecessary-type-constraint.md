Pattern: Redundant generic type constraint

Issue: -

## Description

Generic type parameters are implicitly constrained to `unknown`. Explicitly extending from `any` or `unknown` is redundant and adds unnecessary verbosity to the code.

## Examples

Example of **incorrect** code:
```typescript
interface Foo<T extends any> {}
type Bar<T extends unknown> = T;
class Baz<T extends unknown> {}
function qux<T extends any>() {}
```

Example of **correct** code:
```typescript
interface Foo<T> {}
type Bar<T> = T;
class Baz<T> {}
function qux<T>() {}
```