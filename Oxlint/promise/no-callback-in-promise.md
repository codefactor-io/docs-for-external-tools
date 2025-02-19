Pattern: Callback in Promise handler

Issue: -

## Description

Calling callbacks inside Promise handlers (`.then()` or `.catch()`) can lead to unexpected behavior like multiple invocations. Keep async code consistent by using either promises or callbacks, not both.

## Examples

Example of **incorrect** code:
```javascript
function processWithCallback(callback) {
  Promise.resolve(data)
    .then(() => callback(null, result))
    .catch(err => callback(err));
}
```

Example of **correct** code:
```javascript
// Using promises
async function process() {
  try {
    const result = await Promise.resolve(data);
    return result;
  } catch (err) {
    throw err;
  }
}

// Or using callbacks
function processWithCallback(callback) {
  try {
    callback(null, result);
  } catch (err) {
    callback(err);
  }
}
```