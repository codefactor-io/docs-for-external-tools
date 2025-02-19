Pattern: Inline type import leaving side effects

Issue: -

## Description

When using inline type qualifiers with `--verbatimModuleSyntax`, TypeScript may leave behind unnecessary side-effect imports. Using a top-level `import type` qualifier ensures clean transpilation without side effects.

## Examples

Example of **incorrect** code:
```ts
import { type A, type B } from "mod";
import { type A as AA } from "mod";
```

Example of **correct** code:
```ts
import type { A, B } from "mod";
import type { A as AA } from "mod";
```