Pattern: Direct comparison with `NaN`

Issue: -

## Description

In JavaScript, `NaN` is not equal to itself or any other value, making direct comparisons with `NaN` always return false. Use `Number.isNaN()` or the global `isNaN()` function to properly check for `NaN` values.

## Examples

Example of **incorrect** code:
```javascript
if (foo == NaN) {
  // always false
}

if (foo === NaN) {
  // always false
}

if (foo != NaN) {
  // always true
}

if (value >= NaN) {
  // always false
}
```

Example of **correct** code:
```javascript
if (Number.isNaN(foo)) {
  // proper check
}

if (isNaN(value)) {
  // global function works too
}

// Or check the type
if (typeof foo === 'number' && isNaN(foo)) {
  // more precise check
}
```