Pattern: Use of async function as Promise executor

Issue: -

## Description

The `new Promise` constructor accepts an executor function that controls the state of the created Promise through `resolve` and `reject` parameters. While the executor can be an async function, this is usually a mistake because:

- If an async executor function throws an error, the error will be lost and won't cause the newly-constructed Promise to reject
- Use of `await` in a Promise executor usually indicates that the `new Promise` constructor is unnecessary or its scope can be reduced

## Examples

Example of **incorrect** code:
```javascript
const result = new Promise(async function executor(resolve, reject) {
  const result = await readFile("foo.txt");
  resolve(result);
});
```

The above code is problematic because any errors thrown during the async execution will be lost and the Promise won't reject properly.