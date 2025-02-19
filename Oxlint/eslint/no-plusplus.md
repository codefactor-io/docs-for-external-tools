Pattern: Use of increment/decrement operators

Issue: -

## Description

The unary increment (++) and decrement (--) operators can lead to unexpected behavior due to automatic semicolon insertion and their dual prefix/postfix forms. Using explicit addition or subtraction operations makes the code's intent clearer.

## Examples

Example of **incorrect** code:
```javascript
var x = 0;
x++;

var y = 10;
--y;

for (let i = 0; i < len; i++) {
  doSomething(i);
}
```

Example of **correct** code:
```javascript
var x = 0;
x += 1;

var y = 10;
y -= 1;

for (let i = 0; i < len; i += 1) {
  doSomething(i);
}

// Using other arithmetic
var z = 0;
z = z + 1;
```