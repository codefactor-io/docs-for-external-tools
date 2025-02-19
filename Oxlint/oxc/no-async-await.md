Pattern: Use of `async`/`await`

Issue: -

## Description

Using `async`/`await` syntax is disallowed. Use Promise-based approaches with .then() chains instead where asynchronous code is needed.

## Examples

Example of **incorrect** code:
```javascript
async function getData() {
  const result = await fetch('/api');
  return result.json();
}

const process = async () => {
  await someAsyncOperation();
};
```

Example of **correct** code:
```javascript
function getData() {
  return fetch('/api')
    .then(result => result.json());
}

const process = () => {
  return someAsyncOperation()
    .then(() => {});
};
```