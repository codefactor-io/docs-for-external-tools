Pattern: Inconsistent TypeScript assertion syntax

Issue: -

## Description

Mixing assertion styles (`as` vs angle-bracket) makes code harder to read and maintain.
In some codebases, type assertions are banned in favor of safer alternatives like
type annotations or `satisfies`.

## Examples

Example of **incorrect** code for this rule (default: `assertionStyle: "as"`):
```ts
const value = <Foo>bar;
```

Example of **correct** code for this rule (default: `assertionStyle: "as"`):
```ts
const value = bar as Foo;
```

When `objectLiteralTypeAssertions` or `arrayLiteralTypeAssertions` are set to `never`, then the preferred syntax
for type assertions on object and array literals is to use a type annotation or the `satisfies` operator instead of a type assertion.

Example of **incorrect** code when `objectLiteralTypeAssertions: "never"` and `arrayLiteralTypeAssertions: "never"`:
```ts
const obj = { a: 1 } as Foo;
const arr = [1, 2] as Foo[];
```

Example of **correct** code when `objectLiteralTypeAssertions: "never"` and `arrayLiteralTypeAssertions: "never"`:
```ts
const obj: Foo = { a: 1 };
const obj = { a: 1 } satisfies Foo;
```
