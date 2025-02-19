Pattern: Label name conflicts with variable name

Issue: -

## Description

Using a label that shares a name with a variable in scope creates confusion about what the identifier refers to. Labels should have distinct names to avoid ambiguity and improve code clarity.

## Examples

Example of **incorrect** code:
```javascript
var x = foo;
function bar() {
  x: for (;;) {
    break x;
  }
}

let i = 0;
i: while(true) {
  break i;
}
```

Example of **correct** code:
```javascript
var x = foo;
function bar() {
  loop1: for (;;) {
    break loop1;
  }
}

// Label name doesn't conflict because variable is not in scope
function foo() {
  var y = 10;
}
y: while(true) {
  break y;
}
```