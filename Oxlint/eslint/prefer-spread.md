Pattern: Use of `.apply()` for variadic calls

Issue: -

## Description

The spread operator (`...`) provides a more readable way to pass arrays as arguments to variadic functions compared to using `.apply()`. Use spread syntax unless you need to specify a different `this` context.

## Examples

Example of **incorrect** code:
```javascript
Math.max.apply(Math, numbers);
Object.assign.apply(null, objects);
fn.apply(undefined, args);

const nums = [1, 2, 3];
max.apply(null, nums);

obj.method.apply(obj, items);
```

Example of **correct** code:
```javascript
Math.max(...numbers);
Object.assign({}, ...objects);
fn(...args);

const nums = [1, 2, 3];
max(...nums);

// Apply is ok when this binding matters
fn.apply(thisArg, args);
obj.method.apply(otherObj, args);

// Fixed argument list
fn.apply(null, [1, 2, 3]);
```