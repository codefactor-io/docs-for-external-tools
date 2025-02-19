Pattern: Self import

Issue: -

## Description

A module importing itself creates a circular dependency that can cause runtime issues, including infinite loops, unresolved imports, or undefined values. This often happens accidentally during refactoring.

## Examples

Example of **incorrect** code:
```javascript
// foo.js
import foo from "./foo.js";
const bar = require("./foo");
```

Example of **correct** code:
```javascript
// foo.js
import bar from "./bar.js";
```