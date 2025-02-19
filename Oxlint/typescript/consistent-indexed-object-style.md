Pattern: Mixed indexed object syntax

Issue: -

## Description

TypeScript offers two ways to define indexed object types: using an index signature or using the `Record` utility type. Mixing these styles can harm code readability.

## Examples

Example of **incorrect** code:
```ts
interface Foo {
  [key: string]: unknown;
}
type Bar = {
  [key: string]: unknown;
};
```

Example of **correct** code:
```ts
type Foo = Record<string, unknown>;
type Bar = Record<string, unknown>;
```