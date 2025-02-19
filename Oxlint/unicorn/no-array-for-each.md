Pattern: Use of `Array#forEach`

Issue: -

## Description

Using `for...of` loops instead of `Array#forEach()` provides better performance, readability, and control flow (ability to use `break` or `return`). It also enables better type-narrowing in TypeScript without crossing function boundaries.

## Examples

Example of **incorrect** code:
```javascript
const foo = [1, 2, 3];
foo.forEach((element) => {
  /* ... */
});
```

Example of **correct** code:
```javascript
const foo = [1, 2, 3];
for (const element of foo) {
  /* ... */
}
```