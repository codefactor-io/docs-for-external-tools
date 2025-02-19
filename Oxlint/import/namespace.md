Pattern: Invalid namespace member

Issue: -

## Description

When using namespace imports (`import * as foo`), accessing a non-existent property or attempting to modify a namespace member leads to runtime errors. All referenced names must exist in the imported module.

## Examples

Example of **incorrect** code:
```javascript
// foo.js
export const bar = "bar";

// main.js
import * as foo from "./foo";
foo.notExported();  // Error: name doesn't exist
foo.bar = "value";  // Error: cannot modify namespace
```

Example of **correct** code:
```javascript
// foo.js
export const bar = "bar";

// main.js
import * as foo from "./foo";
console.log(foo.bar);  // Valid: bar exists
```