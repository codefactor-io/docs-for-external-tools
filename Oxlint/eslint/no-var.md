Pattern: Use of `var` declaration

Issue: -

## Description

The `var` keyword creates function-scoped variables that can be accessed before declaration due to hoisting. Using `let` and `const` provides better scoping rules and prevents temporal dead zone issues common with `var`.

## Examples

Example of **incorrect** code:
```javascript
var x = 10;
var config = {};
var i;
for (var j = 0; j < 10; j++) {
  setTimeout(() => console.log(j));
}

function example() {
  var tmp = 'value';
}
```

Example of **correct** code:
```javascript
let x = 10;
const config = {};
let i;
for (let j = 0; j < 10; j++) {
  setTimeout(() => console.log(j));
}

function example() {
  let tmp = 'value';
  const immutable = 'constant';
}
```