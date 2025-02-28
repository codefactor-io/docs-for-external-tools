Pattern: Oversized function

Issue: -

## Description

Large functions often try to do too many things, violating the single responsibility principle. Functions with many lines are harder to understand, test, and maintain. Limiting function size encourages better decomposition into smaller, more focused units.

## Examples

Example of **incorrect** code:
```js
// With { "max": 2 }
function foo() {
  const x = 0;
}

// With { "max": 4 }
function foo() {
  // a comment followed by a blank line

  const x = 0;
}
```

Example of **correct** code:
```js
// With { "max": 3 }
function foo() {
  const x = 0;
}

// With { "max": 5 }
function foo() {
  // a comment followed by a blank line

  const x = 0;
}
```