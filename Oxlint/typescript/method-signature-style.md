Pattern: Inconsistent method signature syntax

Issue: -

## Description

TypeScript provides two ways to define an object/interface function property:

```ts
interface Example {
  // method shorthand syntax
  func(arg: string): number;

  // regular property with function type
  func: (arg: string) => number;
}
```

The two are very similar; most of the time it doesn't matter which one you use. However, when TypeScript's `strictFunctionTypes` option is enabled, there is an important difference: methods are always bivariant in their arguments, while function properties are contravariant. This means that switching from method syntax to property syntax (or vice versa) can cause TypeScript to report new type errors or stop reporting existing ones.

A good practice is to use the TypeScript's `strict` option (which implies `strictFunctionTypes`) which enables correct typechecking for function properties only (method signatures get old behavior).

## Examples

Example of **incorrect** code for this rule with `property` option:

```ts
interface T1 {
  func(arg: string): number;
}
type T2 = {
  func(arg: boolean): void;
};
interface T3 {
  func(arg: number): void;
  func(arg: string): void;
  func(arg: boolean): void;
}
```

Example of **correct** code:

```ts
interface T1 {
  func: (arg: string) => number;
}
type T2 = {
  func: (arg: boolean) => void;
};
// this is equivalent to the overload
interface T3 {
  func: ((arg: number) => void) & ((arg: string) => void) & ((arg: boolean) => void);
}
```