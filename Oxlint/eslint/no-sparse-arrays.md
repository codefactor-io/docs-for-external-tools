Pattern: Array with empty slots

Issue: -

## Description

Sparse arrays contain empty slots, which can lead to confusion as these slots behave differently from slots with undefined values. Empty slots are often created accidentally and can cause unexpected behavior in array operations.

## Examples

Example of **incorrect** code:
```javascript
const items = [1, , 3];
const colors = ["red",, "blue"];
const coords = [1,,,4];

const arr = [
  1,
  ,
  3
];

array = [1, , ];
```

Example of **correct** code:
```javascript
const items = [1, undefined, 3];
const colors = ["red", undefined, "blue"];
const coords = [1, undefined, undefined, 4];

const arr = [
  1,
  undefined,
  3
];

array = [1, undefined];
```