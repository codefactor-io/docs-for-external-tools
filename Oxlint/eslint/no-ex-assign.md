Pattern: Reassignment of exception parameter

Issue: -

## Description

Reassigning the exception parameter in a catch clause makes it impossible to reference the original error afterward. Since there's no alternative way to access the error object, this assignment permanently loses the error information.

## Examples

Example of **incorrect** code:
```javascript
try {
  doSomething();
} catch (e) {
  e = 10;
  e = new Error('different error');
  e = null;
}
```

Example of **correct** code:
```javascript
try {
  doSomething();
} catch (e) {
  const errorCode = 10;
  const newError = new Error('different error');
  handleError(e);
}
```