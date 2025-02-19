Pattern: Use of `void` operator

Issue: -

## Description

The `void` operator is primarily used to obtain the `undefined` value, but this can be done more clearly by using `undefined` directly. Using `void` adds unnecessary complexity and can confuse readers unfamiliar with this JavaScript idiom.

## Examples

Example of **incorrect** code:
```javascript
var undefined = void 0;
function foo() {
  return void 0;
}

const value = void someFunction();
if (value === void 0) {}

void (function() {
  // IIFE
})();
```

Example of **correct** code:
```javascript
var undefined = undefined;
function foo() {
  return undefined;
}

const value = undefined;
if (value === undefined) {}

// For IIFEs, use parentheses
(function() {
  // IIFE
})();
```