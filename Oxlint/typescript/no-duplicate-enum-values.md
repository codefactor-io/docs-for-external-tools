Pattern: Duplicate enum member values

Issue: -

## Description

While TypeScript allows duplicate enum member values, having multiple members with the same value often indicates a mistake and can lead to confusion. Each enum member should have a unique value.

## Examples

Example of **incorrect** code:
```ts
enum Status {
  Active = 0,
  Enabled = 0
}

enum Direction {
  Up = "NORTH",
  North = "NORTH"
}
```

Example of **correct** code:
```ts
enum Status {
  Active = 0,
  Enabled = 1
}

enum Direction {
  Up = "UP",
  North = "NORTH"
}
```