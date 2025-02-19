Pattern: Dynamic function creation using Function constructor

Issue: -

## Description

Creating functions using `new Function()` or `Function()` is similar to using eval and poses security risks. The code string passed to the constructor can be an attack vector, and the resulting functions cannot be optimized by JavaScript engines.

## Examples

Example of **incorrect** code:
```javascript
const sum = new Function('a', 'b', 'return a + b');

const greet = Function('name', 'return "Hello " + name');

const calc = Function.call(null, 'x', 'y', 'return x * y');

const fn = Function.bind(null, 'a', 'return a * 2')();
```

Example of **correct** code:
```javascript
const sum = (a, b) => a + b;

function greet(name) {
  return "Hello " + name;
}

const calc = (x, y) => x * y;

const double = a => a * 2;
```