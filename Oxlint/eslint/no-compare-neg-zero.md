Pattern: Comparison against negative zero

Issue: -

## Description

Comparing against -0 using standard comparison operators (==, ===) doesn't work as intended since both +0 and -0 are considered equal. Use Object.is() instead for detecting negative zero.

## Examples

Example of **incorrect** code:
```javascript
if (x === -0) {
  // Will also match +0
}

while (value == -0) {
  // ...
}
```

Example of **correct** code:
```javascript
if (Object.is(x, -0)) {
  // Correctly identifies -0
}

if (x === 0 && 1 / x < 0) {
  // Alternative way to detect -0
}
```