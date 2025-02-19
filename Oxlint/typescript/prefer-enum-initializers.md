Pattern: Implicit enum member value

Issue: -

## Description

Enum members without explicit values can cause bugs if the enum is modified over time. Each enum member should have an explicit initialization to maintain consistent values.

## Examples

Example of **incorrect** code:
```typescript
enum Status {
  Open = 1,
  Close    // Value is implicitly 2
}

enum Direction {
  Up,      // Value is implicitly 0
  Down     // Value is implicitly 1
}
```

Example of **correct** code:
```typescript
enum Status {
  Open = 1,
  Close = 2
}

enum Direction {
  Up = 0,
  Down = 1
}
```