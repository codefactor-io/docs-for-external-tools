Pattern: Use of `new` with static `Promise` methods

Issue: -

## Description

Using `new` with static `Promise` methods like `Promise.resolve` or `Promise.all` will throw a `TypeError`. Static methods already return Promise instances and shouldn't be used as constructors.

## Examples

Example of **incorrect** code:
```javascript
const p1 = new Promise.resolve(value);
const p2 = new Promise.all([promise1, promise2]);
const p3 = new Promise.race([promise1, promise2]);
```

Example of **correct** code:
```javascript
const p1 = Promise.resolve(value);
const p2 = Promise.all([promise1, promise2]);
const p3 = Promise.race([promise1, promise2]);
```