Pattern: Variable declaration with `require`

Issue: -

## Description

Using `require()` with variable declarations is discouraged in TypeScript. Instead, use ES6-style imports or TypeScript's `import = require()` syntax for better type checking and code maintainability.

## Examples

Example of **incorrect** code:
```typescript
var foo = require("foo");
const bar = require("bar");
let baz = require("baz");
```

Example of **correct** code:
```typescript
import foo from "foo";
import * as bar from "bar";
import baz = require("baz");  // TypeScript-style import
```