Pattern: Redundant `await` operator usage

Issue: -

## Description

The `await` operator should only be used with `Promise` values. Using it with non-promise values or multiple times on the same promise is unnecessary and can make code harder to read.

## Examples

Example of **incorrect** code:
```javascript
async function bad() {
  await await promise;
}
```

Example of **correct** code:
```javascript
async function good() {
  await promise;
}
```