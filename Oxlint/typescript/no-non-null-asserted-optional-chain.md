Pattern: Non-null assertion after optional chaining

Issue: -

## Description

Using a non-null assertion (`!`) after an optional chain (`?.`) is contradictory since optional chaining already handles `null` and `undefined` by returning `undefined`. This combination typically indicates confusion about type safety.

## Examples

Example of **incorrect** code:
```ts
foo?.bar!;
foo?.bar()!;
```

Example of **correct** code:
```ts
foo?.bar;
foo?.bar();
foo!.bar;  // if you're sure foo is non-null
```