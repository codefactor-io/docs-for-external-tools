Pattern: Non-standard `Promise` constructor parameter names

Issue: -

## Description

The `Promise` constructor follows the RevealingConstructor pattern with standard parameter names `resolve` and `reject`. Using different names or incorrect ordering can make code harder to understand and less consistent with the language specification.

## Examples

Example of **incorrect** code:
```javascript
new Promise(function (reject, resolve) {
  /* ... */
}); // incorrect order
new Promise(function (ok, fail) {
  /* ... */
}); // non-standard parameter names
```

Example of **correct** code:
```javascript
new Promise(function (resolve, reject) {});
```