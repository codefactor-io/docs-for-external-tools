Pattern: Method borrowing from instance

Issue: -

## Description

"Borrowing" methods from instances of `Array` or `Object` is less clear than accessing them from the corresponding prototype. Use `Array.prototype` or `Object.prototype` when borrowing methods.

## Examples

Example of **incorrect** code:
```javascript
const array = [].slice.apply(bar);
const type = {}.toString.call(foo);
Reflect.apply([].forEach, arrayLike, [callback]);
```

Example of **correct** code:
```javascript
const array = Array.prototype.slice.apply(bar);
const type = Object.prototype.toString.call(foo);
Reflect.apply(Array.prototype.forEach, arrayLike, [callback]);
const maxValue = Math.max.apply(Math, numbers);
```