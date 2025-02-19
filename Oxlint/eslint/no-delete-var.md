Pattern: Use of `delete` on variable

Issue: -

## Description

The `delete` operator is designed to remove properties from objects. Using it on variables can lead to unexpected behavior and is not the correct way to unset variables. Use assignment to `undefined` or block scoping instead.

## Examples

Example of **incorrect** code:
```javascript
var x;
delete x;

let y = 42;
delete y;

function test() {
  var z = 43;
  delete z;
}
```

Example of **correct** code:
```javascript
let obj = { x: 1, y: 2 };
delete obj.x;

var x = 42;
x = undefined;  // To unset a variable

{
  let y = 43;
}  // Variable goes out of scope
```