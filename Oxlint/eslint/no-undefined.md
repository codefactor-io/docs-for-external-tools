Pattern: Use of `undefined` identifier

Issue: -

## Description

Using `undefined` as an identifier is problematic because it can be redefined in non-strict mode, leading to unexpected behavior. Use `void 0` or type checking with `typeof` instead of direct undefined comparisons.

## Examples

Example of **incorrect** code:
```javascript
var foo = undefined;

if (bar === undefined) {
  handle();
}

function example(undefined) {
  // parameter shadows global undefined
}

let undefined = "redefining";

obj.callback(undefined, value);
```

Example of **correct** code:
```javascript
var foo = void 0;

if (typeof bar === "undefined") {
  handle();
}

function example(param) {
  if (param === void 0) {
    // handle undefined
  }
}

obj.callback(void 0, value);

// Using destructuring default
const { prop = 'default' } = obj;
```