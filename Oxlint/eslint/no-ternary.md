Pattern: Use of ternary operator

Issue: -

## Description

The ternary operator provides a shorthand way to write conditional expressions, but can make code harder to read, especially when nested or used for complex conditions. Using if statements makes the code's intent clearer.

## Examples

Example of **incorrect** code:
```javascript
const value = condition ? trueValue : falseValue;

const status = count > 0 ? 'active' : 'inactive';

const result = x ? a ? b : c : d;

return isValid ? success() : failure();
```

Example of **correct** code:
```javascript
let value;
if (condition) {
  value = trueValue;
} else {
  value = falseValue;
}

let status;
if (count > 0) {
  status = 'active';
} else {
  status = 'inactive';
}

if (isValid) {
  return success();
} else {
  return failure();
}
```