Pattern: `var` declaration not at top of scope

Issue: -

## Description

Due to variable hoisting in JavaScript, `var` declarations should be placed at the top of their scope to make the behavior explicit. This improves code clarity by making it obvious where variables are accessible from.

## Examples

Example of **incorrect** code:
```javascript
function doSomething() {
  console.log(a);
  if (condition) {
    var a = true;
  }
  var b = false;
}

f();
var x;

function test() {
  for (var i = 0; i < 10; i++) {}
  var y = 1;
}
```

Example of **correct** code:
```javascript
function doSomething() {
  var a;
  var b;
  
  console.log(a);
  if (condition) {
    a = true;
  }
  b = false;
}

var x;
f();

function test() {
  var i;
  var y;
  
  for (i = 0; i < 10; i++) {}
  y = 1;
}
```