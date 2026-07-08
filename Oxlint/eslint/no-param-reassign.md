Pattern: Reassignment of function parameter

Issue: -

## Description

Reassigning parameters can lead to unexpected behavior, especially when relying on the
original arguments passed into the function. Mutating parameter properties can be similarly
surprising and harder to reason about.

## Examples

Example of **incorrect** code:
```javascript
function foo(bar) {
  bar = 1;
}

function baz(qux) {
  qux.prop = 2; // when `props` option is enabled
}
```
