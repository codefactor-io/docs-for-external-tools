Pattern: Unnecessary `Error.captureStackTrace()` call

Issue: -

## Description

Calling `Error.captureStackTrace(…)` inside the constructor of a built-in `Error` subclass
is unnecessary, since the `Error` constructor calls it automatically.

## Examples

Example of **incorrect** code:
```javascript
class MyError extends Error {
  constructor() {
    Error.captureStackTrace(this, MyError);
  }
}
```

Example of **correct** code:
```javascript
class MyError extends Error {
  constructor() {
    // No need to call Error.captureStackTrace
  }
}
```
