Pattern: Too many dependencies

Issue: -

## Description

A module with too many dependencies (import or require statements) is a code smell that indicates the module may be doing too much and should be broken into smaller, more focused modules.

## Examples

Example of **incorrect** code:
```javascript
import a from "./a";
import b from "./b";
import c from "./c"; // Exceeds maximum of 2 dependencies
```

Example of **correct** code:
```javascript
import a from "./a";
import b from "./b"; // Within limit of 2 dependencies
```