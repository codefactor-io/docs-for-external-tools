Pattern: Separated function overload signatures

Issue: -

## Description

Function overload signatures should be placed consecutively to improve code readability and maintainability. When signatures are separated by other members, they become harder to find and understand.

## Examples

Example of **incorrect** code:
```typescript
interface Foo {
  foo(s: string): void;
  foo(n: number): void;
  bar(): void;
  foo(sn: string | number): void;
}
```

Example of **correct** code:
```typescript
interface Foo {
  foo(s: string): void;
  foo(n: number): void;
  foo(sn: string | number): void;
  bar(): void;
}
```