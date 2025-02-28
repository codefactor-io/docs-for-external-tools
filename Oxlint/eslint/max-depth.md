Pattern: Excessive nesting depth

Issue: -

## Description

Code with deeply nested blocks becomes difficult to read, understand, and maintain. Too many levels of nesting increase cognitive load and make reasoning about code flow more challenging. Limiting nesting depth encourages cleaner code structure.

## Examples

Example of **incorrect** code:
```js
// With { "max": 3 }
function foo() {
  for (;;) { // Nested 1 deep
    while (true) { // Nested 2 deep
      if (true) { // Nested 3 deep
        if (true) { // Nested 4 deep }
      }
    }
  }
}
```

Example of **correct** code:
```js
// With { "max": 3 }
function foo() {
  for (;;) { // Nested 1 deep
    while (true) { // Nested 2 deep
      if (true) { // Nested 3 deep }
    }
  }
}
```