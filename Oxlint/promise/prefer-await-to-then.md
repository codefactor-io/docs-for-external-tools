Pattern: Use of `Promise.then()` chains

Issue: -

## Description

The `async/await` syntax provides a more readable way to handle promises compared to chaining `.then()`, `.catch()`, and `.finally()` methods. Using `await` makes asynchronous code appear more linear and easier to understand.

## Examples

Example of **incorrect** code:
```javascript
function foo() {
  hey.then((x) => {});
}

// With { strict: true }
async function hi() {
  await thing().then((x) => {});
}
```

Example of **correct** code:
```javascript
async function hi() {
  await thing();
}
```