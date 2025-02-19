Pattern: Mixed type definition syntax

Issue: -

## Description

TypeScript provides two ways to define object types: `interface` and `type`. While they are similar and often interchangeable, mixing both styles in a codebase can reduce readability.

## Examples

Example of **incorrect** code:
```ts
// When preferring interface
type User = {
  id: number;
  name: string;
};

// When preferring type
interface Product {
  id: number;
  name: string;
}
```

Example of **correct** code:
```ts
// When preferring interface
interface User {
  id: number;
  name: string;
}

interface Product {
  id: number;
  name: string;
}
```