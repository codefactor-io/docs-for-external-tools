Pattern: Missing return in array method callback

Issue: -

## Description

Array methods like map, filter, and reduce expect their callback functions to return values. Forgetting to include a return statement is likely a mistake. If you don't need to return values, consider using forEach instead.

## Examples

Example of **incorrect** code:
```javascript
let foo = [1, 2, 3, 4];
foo.map((a) => {
  console.log(a);
});
```

Example of **correct** code:
```javascript
let foo = [1, 2, 3, 4];
foo.map((a) => {
  console.log(a);
  return a * 2;
});

// Or use forEach when no return is needed
foo.forEach((a) => {
  console.log(a);
});
```