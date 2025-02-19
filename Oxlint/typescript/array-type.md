Pattern: Inconsistent array type syntax

Issue: -

## Description

TypeScript provides two ways to define array types: `T[]` and `Array<T>`. Using them inconsistently within a codebase can reduce readability. Choose one style and stick to it.

## Examples

Example of **incorrect** code:
```typescript
const numbers: Array<number> = [1, 2, 3];
const strings: string[] = ["a", "b", "c"];
```

Example of **correct** code:
```typescript
const numbers: number[] = [1, 2, 3];
const strings: string[] = ["a", "b", "c"];
```