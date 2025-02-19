Pattern: Binary expression with constant result

Issue: -

## Description

Some binary expressions always produce the same result due to operator precedence or object reference comparison. This often indicates a programmer error, especially with complex expressions or comparisons to newly constructed objects.

## Examples

Example of **incorrect** code:
```javascript
// Nullish coalescing with constant left side
const x = a + b ?? c;  // (a + b) ?? c never uses c

// Comparing with new object
if (x === []) {  // Always false
  console.log("empty");
}

const valid = foo === new RegExp("^[a-z]+$");  // Always false
const same = {} == {};  // Always false
```

Example of **correct** code:
```javascript
const x = a + (b ?? c);  // Properly grouped

if (x.length === 0) {  // Compare property instead
  console.log("empty");
}

const regex = /^[a-z]+$/;
const valid = foo === regex;

const obj = {};
const same = obj === obj;  // Compare same reference
```