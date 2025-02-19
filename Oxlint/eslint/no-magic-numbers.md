Pattern: Unexplained numeric literal

Issue: -

## Description

Magic numbers are numeric literals that appear in code without explanation. They make code harder to understand and maintain because their meaning is not immediately clear. Using named constants makes the code's intent more obvious and easier to update.

## Examples

Example of **incorrect** code:
```javascript
function calculatePrice(cost) {
  return cost + (cost * 0.25);  // What is 0.25?
}

if (value > 86400) {  // Why 86400?
  doSomething();
}

const scores = [-1, 0, 1, 2, 3];  // What do these numbers mean?
```

Example of **correct** code:
```javascript
const TAX_RATE = 0.25;
function calculatePrice(cost) {
  return cost + (cost * TAX_RATE);
}

const SECONDS_IN_DAY = 86400;
if (value > SECONDS_IN_DAY) {
  doSomething();
}

const INVALID_SCORE = -1;
const NO_SCORE = 0;
const LOW_SCORE = 1;
const MEDIUM_SCORE = 2;
const HIGH_SCORE = 3;
const scores = [INVALID_SCORE, NO_SCORE, LOW_SCORE, MEDIUM_SCORE, HIGH_SCORE];
```