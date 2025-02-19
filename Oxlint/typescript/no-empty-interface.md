Pattern: Empty interface declaration

Issue: -

## Description

Empty interfaces (`{}`) are redundant since any non-nullable value is assignable to an empty interface. They often indicate a misunderstanding of TypeScript's type system or forgotten interface members.

## Examples

Example of **incorrect** code:
```ts
interface Foo {}
interface Bar extends Foo {}
```

Example of **correct** code:
```ts
interface Foo {
  prop: string;
}

interface Bar extends Foo {
  additionalProp: number;
}
```