Pattern: `return` statement in `Promise.finally()`

Issue: -

## Description

Using a `return` statement inside a `finally()` callback is ineffective since the returned value will not be consumed. The `finally()` block should only be used for cleanup code that needs to run regardless of the promise outcome.

## Examples

Example of **incorrect** code:
```javascript
myPromise.finally(function (val) {
  return val;
});
```

Example of **correct** code:
```javascript
Promise.resolve(1).finally(() => {
  console.log(2);
});
```