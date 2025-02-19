Pattern: Unsafe interface and class merging

Issue: -

## Description

Merging class and interface declarations can lead to runtime errors that TypeScript doesn't detect, as it doesn't verify whether all interface properties are properly initialized in the class.

## Examples

Example of **incorrect** code:
```ts
interface Foo {
  prop: string;
}
class Foo {
  // Missing prop initialization
}
```

Example of **correct** code:
```ts
interface Foo {
  prop: string;
}
class Bar implements Foo {
  prop = "value";
}
```