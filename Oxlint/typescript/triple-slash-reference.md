Pattern: Use of triple-slash reference directive

Issue: -

## Description

Triple-slash reference directives are an outdated way to include external files and declare module dependencies. Use ES6-style module imports instead for better maintainability and tooling support.

## Examples

Example of **incorrect** code:
```ts
/// <reference path="other.ts" />
/// <reference types="node" />
/// <reference lib="dom" />

globalThis.value;
```

Example of **correct** code:
```ts
import { Something } from "./other";
import type { Node } from "node";
```