Pattern: Non-standard `Promise` method usage

Issue: -

## Description

Using non-standard `Promise` static methods can increase maintenance costs and reduce code portability. Stick to standardized `Promise` methods defined in the ECMAScript specification.

## Examples

Example of **incorrect** code:
```js
Promise.done();
```

Example of **correct** code:
```js
Promise.resolve();
```