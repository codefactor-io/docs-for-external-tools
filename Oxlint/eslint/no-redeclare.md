Pattern: Variable redeclaration

Issue: -

## Description

Redeclaring variables can create confusion about where a variable is initialized and what its current value might be. While `var` allows redeclaration, it's better to use a single declaration to make the code's intent clear.

## Examples

Example of **incorrect** code:
```javascript
var x = 1;
var x = 2;

function foo(a) {
  var a = 1;  // Redeclaring parameter
}

var y = 5;
function y() {}  // Redeclaring as function

if (true) {
  var z = 1;
}
var z = 2;  // Redeclaring from block scope
```

Example of **correct** code:
```javascript
var x = 1;
x = 2;  // Reassignment, not redeclaration

function foo(a) {
  let b = 1;  // New variable
}

let y = 5;
const calculate = function() {};

if (true) {
  let z = 1;
}
let y = 2;  // Different block scope
```