Pattern: Non-Error Promise rejection reason

Issue: -

## Description

Rejecting Promises with non-Error values makes debugging difficult since there's no stack trace. Using Error objects (or subclasses) for rejections provides consistent error handling and better debugging information.

## Examples

Example of **incorrect** code:
```javascript
Promise.reject('something bad happened');
Promise.reject(500);
Promise.reject();

new Promise((resolve, reject) => {
  reject('error');
});

Promise.reject({ code: 'INVALID' });
```

Example of **correct** code:
```javascript
Promise.reject(new Error('something bad happened'));
Promise.reject(new TypeError('invalid type'));

new Promise((resolve, reject) => {
  reject(new Error('error'));
});

// Rejecting with non-literal values is ok
const error = getError();
Promise.reject(error);

// Error subclasses are ok
class CustomError extends Error {}
Promise.reject(new CustomError());
```