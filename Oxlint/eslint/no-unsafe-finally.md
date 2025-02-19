Pattern: Control flow statement in `finally` block

Issue: -

## Description

Using return, throw, break, or continue inside a finally block overrides control flow statements in try and catch blocks. This is because finally blocks execute after try/catch but before their control flow statements take effect.

## Examples

Example of **incorrect** code:
```javascript
function foo() {
  try {
    return 1;
  } catch(err) {
    return 2;
  } finally {
    return 3;  // This overrides any return in try/catch
  }
}

function bar() {
  try {
    throw new Error("error");
  } finally {
    throw new Error("final");  // Original error is lost
  }
}

for (let i = 0; i < 10; i++) {
  try {
    continue;
  } finally {
    break;  // Overrides continue
  }
}
```

Example of **correct** code:
```javascript
function foo() {
  try {
    return 1;
  } catch(err) {
    return 2;
  } finally {
    cleanup();  // No control flow statements
  }
}

function bar() {
  let error;
  try {
    throw new Error("error");
  } catch(err) {
    error = err;
  } finally {
    cleanup();
  }
  if (error) throw error;
}
```