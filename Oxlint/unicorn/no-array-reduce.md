Pattern: Use of `Array#reduce()` or `Array#reduceRight()`

Issue: -

## Description

Using `Array#reduce()` or `Array#reduceRight()` often results in code that is harder to read and less performant. These methods can usually be replaced with `.map`, `.filter`, or a `for-of` loop for better clarity and performance. The exception is simple number summation, which is allowed by default.

## Examples

Example of **incorrect** code:
```javascript
array.reduce(reducer, initialValue);
array.reduceRight(reducer, initialValue);
```

Example of **correct** code:
```javascript
// Using map
const result = array.map(x => x.value);

// Using for-of
let result = 0;
for (const num of numbers) {
  result += num;
}
```