Pattern: Use of generic `Function` type

Issue: -

## Description

The built-in `Function` type accepts any number of arguments and returns `any`, making it unsafe. Instead, specify function parameters and return types explicitly using function type syntax.

## Examples

Example of **incorrect** code:
```ts
let stringToNumber: Function;
stringToNumber = (text: string) => text.length;

let identity: Function;
identity = (value) => value;
```

Example of **correct** code:
```ts
let stringToNumber: (text: string) => number;
stringToNumber = (text) => text.length;

let identity: <T>(value: T) => T;
identity = (value) => value;
```