Pattern: Redundant comparison

Issue: -

## Description

Double comparisons using logical operators can often be simplified to a single comparison. These redundant comparisons make code harder to read and maintain.

## Examples

Example of **incorrect** code:
```javascript
if (x === y || x < y) {
  // Can be simplified
}

if (x < y || x === y) {
  // Same redundant pattern
}
```

Example of **correct** code:
```javascript
if (x <= y) {
  // Simplified
}

if (y >= x) {
  // Alternative form
}
```