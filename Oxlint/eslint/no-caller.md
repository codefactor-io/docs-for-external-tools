Pattern: Use of `arguments.caller` or `arguments.callee`

Issue: -

## Description

The `arguments.caller` and `arguments.callee` properties are deprecated and forbidden in strict mode. They prevent code optimizations and should be replaced with named functions or arrow functions.

## Examples

Example of **incorrect** code:
```javascript
function foo(n) {
  if (n <= 0) return;
  arguments.callee(n - 1);
}

[1, 2, 3, 4, 5].map(function(n) {
  return !(n > 1) ? 1 : arguments.callee(n - 1) * n;
});
```

Example of **correct** code:
```javascript
function foo(n) {
  if (n <= 0) return;
  foo(n - 1);
}

[1, 2, 3, 4, 5].map(function factorial(n) {
  return !(n > 1) ? 1 : factorial(n - 1) * n;
});
```