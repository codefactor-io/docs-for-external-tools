Pattern: Use of `const enum`

Issue: -

## Description

`const enum` in TypeScript is incompatible with bundlers and isolatedModules mode. The values are inlined at use sites, which can lead to importing nonexistent values after bundling.

## Examples

Example of **incorrect** code:
```typescript
const enum Direction {
  Up,
  Down,
  Left,
  Right
}
```

Example of **correct** code:
```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}
```