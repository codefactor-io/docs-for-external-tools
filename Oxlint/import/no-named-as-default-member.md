Pattern: Named export access via default

Issue: -

## Description

Accessing a named export as a property of the default export is incorrect and will not work as expected. Named exports should be imported directly rather than accessed through the default export object.

## Examples

Example of **incorrect** code:
```javascript
// bar.js
export function bar() { return null; }
export default () => 1;

// main.js
import foo from "./bar";
const bar = foo.bar;  // Attempting to access named export via default
```

Example of **correct** code:
```javascript
// bar.js
export function bar() { return null; }
export default () => 1;

// main.js
import { bar } from "./bar";  // Direct import of named export
```