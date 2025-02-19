Pattern: Object literal comparison

Issue: -

## Description

Comparing a variable directly with an object or array literal will always return false because each literal creates a new reference. Use appropriate methods to check object or array properties instead.

## Examples

Example of **incorrect** code:
```javascript
if (obj === {}) {
  // Always false
}

if (array !== []) {
  // Always true
}
```

Example of **correct** code:
```javascript
if (Object.keys(obj).length === 0) {
  // Properly checks if object is empty
}

if (array.length === 0) {
  // Properly checks if array is empty
}
```