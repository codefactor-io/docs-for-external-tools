Pattern: Use of `arguments` object

Issue: -

## Description

The `arguments` object is an array-like object that lacks array methods, making it cumbersome to use. Rest parameters provide actual arrays with all array methods available and make variable argument handling more explicit.

## Examples

Example of **incorrect** code:
```javascript
function sum() {
  console.log(arguments);
  return Array.prototype.slice.call(arguments).reduce((a, b) => a + b);
}

function log() {
  const args = [].slice.call(arguments);
  args.forEach(console.log);
}

function apply(fn) {
  return fn.apply(null, arguments);
}
```

Example of **correct** code:
```javascript
function sum(...numbers) {
  console.log(numbers);
  return numbers.reduce((a, b) => a + b);
}

function log(...args) {
  args.forEach(console.log);
}

function apply(fn, ...args) {
  return fn(...args);
}

// Arguments as parameter name is fine
function example(arguments) {
  console.log(arguments);
}
```