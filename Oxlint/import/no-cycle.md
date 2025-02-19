Pattern: Circular dependency

Issue: -

## Description

A circular dependency occurs when module A imports from module B, which directly or indirectly imports back to module A. This creates confusing architectures where bugs become hard to find and can lead to importing undefined values.

## Examples

Example of **incorrect** code:
```javascript
// dep-a.js
import { b } from "./dep-b.js";
export function a() { /* ... */ }

// dep-b.js
import { a } from "./dep-a.js";
export function b() { /* ... */ }
```

Example of **correct** code:
```javascript
// dep-a.js
import { b } from "./dep-b.js";
export function a() { /* ... */ }

// dep-b.js
export function b() { /* ... */ }
```