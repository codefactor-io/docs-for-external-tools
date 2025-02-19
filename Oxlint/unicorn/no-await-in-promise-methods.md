Pattern: `await` in `Promise` method arguments

Issue: -

## Description

Using `await` on promises passed to `Promise.all()`, `Promise.allSettled()`, `Promise.any()`, or `Promise.race()` is likely a mistake as it defeats the purpose of these methods which are designed to handle multiple promises concurrently.

## Examples

Example of **incorrect** code:
```javascript
async function foo() {
  Promise.all([await promise, anotherPromise]);
  Promise.allSettled([await promise, anotherPromise]);
  Promise.any([await promise, anotherPromise]);
  Promise.race([await promise, anotherPromise]);
}
```

Example of **correct** code:
```javascript
async function foo() {
  Promise.all([promise, anotherPromise]);
  Promise.allSettled([promise, anotherPromise]);
  Promise.any([promise, anotherPromise]);
  Promise.race([promise, anotherPromise]);
}
```