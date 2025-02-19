Pattern: `Object.assign` with object literal first argument

Issue: -

## Description

When the first argument to `Object.assign` is an empty object literal, the spread operator (`...`) provides a more concise and readable syntax. Similarly, `Object.assign` with a single object literal argument is unnecessary.

## Examples

Example of **incorrect** code:
```javascript
Object.assign({}, foo);
Object.assign({}, { x: 1, y: 2 });
Object.assign({ a: 1 }, baz);
Object.assign({}, foo, { bar: 2 });

// Single object literal argument
Object.assign({});
Object.assign({ foo: bar });
```

Example of **correct** code:
```javascript
({ ...foo });
({ x: 1, y: 2, ...baz });
({ ...foo, bar: 2 });

// Object.assign without object literal first arg
Object.assign(target, { a: 1 });
Object.assign(foo, bar);
Object.assign(obj, { ...props });
```