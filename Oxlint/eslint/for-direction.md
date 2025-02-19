Pattern: Incorrect `for` loop counter direction

Issue: -

## Description

A `for` loop with a stop condition that can never be reached, such as one with a counter that moves in the wrong direction, will run infinitely. While there are occasions when an infinite loop is intended, the convention is to construct such loops as `while` loops. More typically, an infinite `for` loop is a bug.

## Examples

Example of **incorrect** code:
```js
for (var i = 0; i < 10; i--) {}
for (var i = 10; i >= 0; i++) {}
for (var i = 0; i > 10; i++) {}
for (var i = 0; 10 > i; i--) {}
const n = -2;
for (let i = 0; i < 10; i += n) {}
```

Example of **correct** code:
```js
for (var i = 0; i < 10; i++) {}
for (var i = 0; 10 > i; i++) {
  // with counter "i" on the right
}
for (let i = 10; i >= 0; i += this.step) {
  // direction unknown
}
for (let i = MIN; i <= MAX; i -= 0) {
  // not increasing or decreasing
}
```