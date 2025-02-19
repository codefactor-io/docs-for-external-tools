Pattern: Use of callback-style async code

Issue: -

## Description

Using callbacks can lead to complex, nested structures known as "callback hell" that make code difficult to read and maintain. The `async/await` syntax provides a clearer and more concise way to write asynchronous code, with better error handling through try/catch blocks.

## Examples

Example of **incorrect** code:
```js
cb();
callback();
doSomething(arg, (err) => {});
function doSomethingElse(cb) {}
```

Example of **correct** code:
```js
await doSomething(arg);
async function doSomethingElse() {}
function* generator() {
  yield yieldValue((err) => {});
}
eventEmitter.on("error", (err) => {});
```