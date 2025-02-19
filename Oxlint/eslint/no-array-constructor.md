Pattern: Creation of array using `Array` constructor

Issue: -

## Description

Using the `Array` constructor can lead to unexpected behavior due to its single-argument pitfall and potential global redefinition. Array literal notation is preferred except when creating sparse arrays of a specific size.

## Examples

Example of **incorrect** code:
```javascript
let arr = new Array();
let numbers = new Array(1, 2, 3);
let items = new Array('item');
```

Example of **correct** code:
```javascript
let arr = [];
let numbers = [1, 2, 3];
let sparseArr = new Array(10);  // Creating sparse array with specific size
let items = Array.from(iterable);
```