Pattern: Single promise in `Promise` method array

Issue: -

## Description

Using `Promise.all()`, `Promise.any()`, or `Promise.race()` with a single-element array is unnecessary and likely a mistake. Use `await` directly on the promise or `Promise.resolve()` for non-promises.

## Examples

Example of **incorrect** code:
```javascript
async function bad() {
  const foo = await Promise.all([promise]);
  const foo = await Promise.any([promise]);
  const foo = await Promise.race([promise]);
  const promise = Promise.all([nonPromise]);
}
```

Example of **correct** code:
```javascript
async function good() {
  const foo = await promise;
  const promise = Promise.resolve(nonPromise);
  const foo = await Promise.all(promises);
  const foo = await Promise.any([promise, anotherPromise]);
}
```