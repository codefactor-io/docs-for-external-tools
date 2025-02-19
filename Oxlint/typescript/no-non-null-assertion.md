Pattern: Use of non-null assertion operator

Issue: -

## Description

The `!` operator forces TypeScript to treat a value as non-nullable, bypassing type safety checks. Instead, structure code to handle nullable cases explicitly through conditionals or optional chaining.

## Examples

Example of **incorrect** code:
```ts
const value = maybeNullable!;
obj!.property;
arr![0];
```

Example of **correct** code:
```ts
if (maybeNullable) {
  const value = maybeNullable;
}
obj?.property;
arr?.[0];
```