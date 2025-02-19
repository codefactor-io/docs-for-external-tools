Pattern: Non-existent named import

Issue: -

## Description

Importing or exporting names that don't exist in the referenced module leads to runtime errors. The imported or exported name must be included in the set of named exports from the referenced module.

## Examples

Example of **incorrect** code:
```javascript
// foo.js
export const foo = "foo";

// bar.js
import { notFoo } from "./foo";
export { notFoo as bar } from "./foo";
```

Example of **correct** code:
```javascript
// foo.js
export const foo = "foo";

// bar.js
import { foo } from "./foo";
export { foo as bar } from "./foo";
```