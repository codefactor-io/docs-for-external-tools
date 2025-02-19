Pattern: Redundant empty export

Issue: -

## Description

An empty `export {}` statement is useful to turn a script file into a module in TypeScript. However, if the file already contains other imports or exports, the empty export becomes redundant and should be removed.

## Examples

Example of **incorrect** code:
```ts
export const value = "Hello";
export {};  // redundant

import { something } from "./other";
export {};  // redundant
```

Example of **correct** code:
```ts
export const value = "Hello";

// Empty file becomes module
export {};
```