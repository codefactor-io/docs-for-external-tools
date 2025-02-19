Pattern: Promise in error-first callback

Issue: -

## Description

Mixing Promises within error-first callback functions makes the code harder to follow and complicates error handling. Keep async code consistent by using either callbacks or Promises/async-await throughout.

## Examples

Example of **incorrect** code:
```javascript
readFile('file.txt', (err, data) => {
  if (err) handleError(err);
  else {
    Promise.resolve(data)
      .then(processData);
  }
});
```

Example of **correct** code:
```javascript
// Using promises consistently
const data = await readFile('file.txt');
await processData(data);

// Or using callbacks consistently
readFile('file.txt', (err, data) => {
  if (err) handleError(err);
  else processData(data, handleResult);
});
```