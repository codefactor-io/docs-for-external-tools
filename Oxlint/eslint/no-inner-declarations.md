Pattern: Function or variable declaration inside nested block

Issue: -

## Description

Declaring variables or functions inside nested blocks can lead to confusing behavior due to hoisting. While block-scoped declarations (let, const) are not affected, function and var declarations should be moved to the root of the program or function body for clarity.

## Examples

Example of **incorrect** code:
```javascript
if (test) {
  function foo() {}
  var bar = 42;
}

while (test) {
  function baz() {}
}

function outer() {
  if (test) {
    function inner() {}
  }
}
```

Example of **correct** code:
```javascript
// At root level
function foo() {}
var bar = 42;

if (test) {
  // Using block-scoped declarations is fine
  let x = 42;
  const y = () => {};
}

function outer() {
  // At function body level
  function inner() {}
  
  if (test) {
    inner();
  }
}
```