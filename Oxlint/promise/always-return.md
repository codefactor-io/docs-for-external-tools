Pattern: Missing return in Promise callback

Issue: -

## Description

Broken Promise Chain.
Inside the first `then()` callback, a function is called but not returned.
This causes the next `then()` in the chain to execute immediately without waiting for the called function to complete.

## Examples

Example of **incorrect** code:
```javascript
myPromise.then(function (val) {});
myPromise.then(() => {
  doSomething();
});
myPromise.then((b) => {
  if (b) {
    return "yes";
  } else {
    forgotToReturn();
  }
});
```

Example of **correct** code:
```javascript
myPromise.then((val) => val * 2);
myPromise.then(function (val) {
  return val * 2;
});
myPromise.then(doSomething); // could be either
myPromise.then((b) => {
  if (b) {
    return "yes";
  } else {
    return "no";
  }
});
```
