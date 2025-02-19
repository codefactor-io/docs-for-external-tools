Pattern: Erasing operation

Issue: -

## Description

Operations that always result in zero (like multiplying by 0) or other constant values are likely mistakes. These operations erase the original value and can be replaced with the constant directly.

## Examples

Example of **incorrect** code:
```javascript
let value = someNumber * 0;
let sum = total - total;
let result = 100 + x - x;
```

Example of **correct** code:
```javascript
let value = 0;
let sum = 0;
let result = 100;
```