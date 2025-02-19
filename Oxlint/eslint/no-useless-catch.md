Pattern: Catch clause that only rethrows

Issue: -

## Description

A catch clause that only rethrows the caught error is unnecessary and can be removed. The error will propagate up normally without the try/catch. If you need to catch specific errors, ensure the catch block adds value through error handling.

## Examples

Example of **incorrect** code:
```javascript
try {
  doSomething();
} catch (error) {
  throw error;
}

try {
  mayFail();
} catch (e) {
  throw e;  // Just rethrows
}

function example() {
  try {
    return doWork();
  } catch (ex) {
    throw ex;
  }
}
```

Example of **correct** code:
```javascript
// No try/catch needed
doSomething();

try {
  mayFail();
} catch (e) {
  console.error(e);
  throw e;  // Logs before rethrowing
}

try {
  doWork();
} catch (e) {
  if (e instanceof ValidationError) {
    handleValidationError(e);
  } else {
    throw e;  // Only rethrowing some errors
  }
}
```