Pattern: Non-literal enum member value

Issue: -

## Description

Enum members should only use literal values rather than expressions or references. Using variables or expressions can lead to confusion since enums create their own scope where each member becomes a variable.

## Examples

Example of **incorrect** code:
```ts
const outsideValue = 2;
enum Status {
  outer = outsideValue,
  first = 1,
  second = first,
  third = second
}
```

Example of **correct** code:
```ts
enum Status {
  first = 1,
  second = 2,
  third = 3,
  error = "ERROR"
}
```