Pattern: Inconsistent type import style

Issue: -

## Description

TypeScript provides multiple ways to import types. Using different styles for type imports within the same codebase reduces readability and maintainability.

## Examples

Example of **incorrect** code:
```ts
import { Foo } from "Foo";
type T = Foo;

type S = import("Foo");
```

Example of **correct** code:
```ts
import type { Foo } from "Foo";
type T = Foo;
```