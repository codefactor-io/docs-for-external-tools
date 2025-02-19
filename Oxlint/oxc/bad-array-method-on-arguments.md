Pattern: Array method on arguments

Issue: -

## Description

The arguments object is array-like but not an actual array. Array methods like map, reduce, or filter cannot be called directly on arguments. Convert arguments to an array first.

## Examples

Example of **incorrect** code:
```javascript
function sum() {
  return arguments.filter(x => x > 0)
                 .reduce((a, b) => a + b);
}
```

Example of **correct** code:
```javascript
function sum() {
  const args = Array.from(arguments);
  return args.filter(x => x > 0)
            .reduce((a, b) => a + b);
}
```