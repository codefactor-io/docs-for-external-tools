Pattern: Inconsistent generic type placement

Issue: -

## Description

When constructing a generic class, type arguments can be specified either in the type annotation or in the constructor call. Using both styles inconsistently can reduce code readability.

## Examples

Example of **incorrect** code:
```ts
const a: Foo<string> = new Foo();
const b = new Foo<string>();  // when preferring annotation
```

Example of **correct** code:
```ts
const a: Foo<string> = new Foo();  // when preferring annotation
const b: Bar<string> = new Bar();  // when preferring annotation
```