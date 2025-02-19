Pattern: `new Promise` constructor

Issue: -

## Description

Using `new Promise()` constructor is less idiomatic in modern JavaScript. Prefer `async/await` syntax for better readability and error handling, unless explicitly needed for converting callback-based APIs to Promises.

## Examples

Example of **incorrect** code:
```javascript
function getData() {
  return new Promise((resolve, reject) => {
    doSomething((err, result) => {
      if (err) reject(err);
      else resolve(result);
    });
  });
}
```

Example of **correct** code:
```javascript
async function getData() {
  const result = await doSomething();
  return result;
}

// When necessary for callback APIs
const util = require('util');
const getData = util.promisify(callbackBasedFunction);
```