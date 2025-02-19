Pattern: Missing `throw` keyword

Issue: -

## Description

Creating a new `Error` object without the `throw` keyword doesn't actually throw the error. This is usually a mistake as the error will be created but not thrown, leading to silent failures.

## Examples

Example of **incorrect** code:
```javascript
function validate() {
  if (!valid) {
    new Error("Invalid input");
  }
}

const check = () => {
  new TypeError("Type mismatch");
};
```

Example of **correct** code:
```javascript
function validate() {
  if (!valid) {
    throw new Error("Invalid input");
  }
}

const check = () => {
  throw new TypeError("Type mismatch");
};
```