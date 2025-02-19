Pattern: Yoda condition comparison

Issue: -

## Description

Yoda conditions place literals first in comparisons (like `if ("red" === color)`). While this prevents accidental assignments, modern linting tools catch assignment mistakes. Non-Yoda conditions are more readable as they follow natural language order.

## Examples

Example of **incorrect** code:
```javascript
if ("red" === color) {
  // ...
}

if (5 > count) {
  // ...
}

while (true === isValid) {
  // ...
}

if ("string" === typeof value) {
  // ...
}
```

Example of **correct** code:
```javascript
if (color === "red") {
  // ...
}

if (count > 5) {
  // ...
}

while (isValid === true) {
  // ...
}

if (typeof value === "string") {
  // ...
}

// Range comparisons can be exempt
if (0 <= x && x <= 1) {
  // ...
}
```