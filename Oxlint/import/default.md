Pattern: Missing default export

Issue: -

## Description

Using a default import when the imported module has no default export leads to runtime errors and makes code harder to maintain. This mismatch between import and export styles can cause unexpected behavior.

## Examples

Example of **incorrect** code:
```javascript
// ./bar.js
export function bar() {
  return null;
}

// ./foo.js
import bar from "./bar"; // No default export exists
```

Example of **correct** code:
```javascript
// ./bar.js
export default function bar() {
  return null;
}

// ./foo.js
import bar from "./bar";
```