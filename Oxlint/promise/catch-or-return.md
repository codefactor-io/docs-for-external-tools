Pattern: Uncaught Promise chain

Issue: -

## Description

Promise chains must either have error handling with `.catch()` or be returned from a function. Unhandled rejections can cause silent failures or crash the application.

## Examples

Example of **incorrect** code:
```javascript
function processData() {
  getData()
    .then(transform)
    .then(save);  // No error handling
}

promise.then(value => {
  throw new Error('oops');
});
```

Example of **correct** code:
```javascript
function processData() {
  return getData()
    .then(transform)
    .then(save);  // Returned to caller

  // Or with error handling
  getData()
    .then(transform)
    .then(save)
    .catch(handleError);
}
```