Pattern: Extension of native object prototype

Issue: -

## Description

Extending built-in native objects by adding properties to their prototypes can lead to unexpected behavior, naming conflicts, and compatibility issues across different JavaScript environments. Create utility functions or separate objects instead.

## Examples

Example of **incorrect** code:
```javascript
Object.prototype.extraMethod = function() {};
Array.prototype.customFilter = function() {};
String.prototype.trim = function() {};

Object.defineProperty(Array.prototype, 'sum', {
  value: function() {}
});
```

Example of **correct** code:
```javascript
class CustomArray extends Array {
  customFilter() {}
}

const arrayUtils = {
  sum: function(array) {}
};

function trim(str) {
  return str.trim();
}

class Enhanced {
  extraMethod() {}
}
```