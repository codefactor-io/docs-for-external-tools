Pattern: File exceeds maximum line count

Issue: -

## Description

Large files tend to handle too many responsibilities and can be difficult to understand. While there is no objective maximum, most style guides recommend keeping files between 100 and 500 lines to maintain readability and support the single responsibility principle.

## Examples

Example of **incorrect** code:
```javascript
// A file with 600 lines
class MyClass {
  // ... 550 lines of code ...
}

function helperFunction() {
  // ... 50 more lines ...
}
```

Example of **correct** code:
```javascript
// A file with 200 lines
class MyClass {
  // ... 150 lines of code ...
}

function helperFunction() {
  // ... 50 lines of code ...
}
```