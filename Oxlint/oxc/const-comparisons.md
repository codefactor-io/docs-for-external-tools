Pattern: Impossible comparison

Issue: -

## Description

Comparisons that are logically impossible or redundant should be avoided. This includes comparisons that will always evaluate to the same result and double comparisons against constants that conflict with each other.

## Examples

Example of **incorrect** code:
```javascript
if (x <= 400 && x > 500) {
  // Impossible condition
}

if (a < a) {
  // Always false
}

if (status >= 200 && status <= 100) {
  // Impossible range
}
```

Example of **correct** code:
```javascript
if (x >= 400 && x < 500) {
  // Valid range check
}

if (a < b) {
  // Valid comparison
}

if (status >= 200 && status <= 299) {
  // Valid status check
}
```