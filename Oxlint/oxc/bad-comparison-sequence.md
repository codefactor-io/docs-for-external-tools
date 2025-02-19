Pattern: Chained comparison operators

Issue: -

## Description

Comparison operators cannot be chained to compare multiple values at once. Each comparison returns a boolean, so subsequent comparisons are comparing against true/false rather than the actual values.

## Examples

Example of **incorrect** code:
```javascript
if (x === y === z) {
  // Actually checks if (x === y) === z
}

if (a < b < c) {
  // Actually checks if (a < b) < c
}
```

Example of **correct** code:
```javascript
if (x === y && y === z) {
  // Properly compares all values
}

if (a < b && b < c) {
  // Properly checks range
}
```