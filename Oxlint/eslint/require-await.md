Pattern: Async function without `await`

Issue: -

## Description

Async functions that don't use await might not need to be async. The primary purpose of async functions is to use the await operator. An async function without await is likely an oversight from refactoring or indicates the function could be synchronous.

## Examples

Example of **incorrect** code:
```javascript
async function getData() {
  return 42;
}

const getInfo = async () => {
  processSync();
  return result;
};

async function processItem(item) {
  syncOperation(item);
}
```

Example of **correct** code:
```javascript
async function getData() {
  const data = await fetchData();
  return data;
}

const getInfo = async () => {
  const info = await fetchInfo();
  return processSync(info);
};

// Regular function for sync operations
function processItem(item) {
  syncOperation(item);
}

// Async generator functions are exempt
async function* generator() {
  yield 42;
}
```