Pattern: IIFE with parenthesized arrow function body

Issue: -

## Description

Using Immediately Invoked Function Expressions (IIFEs) with parenthesized arrow function bodies creates hard-to-read code. Consider using regular function bodies or separating the logic into named functions.

## Examples

Example of **incorrect** code:
```javascript
const foo = ((bar) => (bar ? bar.baz : baz))(getBar());
const foo = ((bar, baz) => ({ bar, baz }))(bar, baz);
```

Example of **correct** code:
```javascript
const bar = getBar();
const foo = bar ? bar.baz : baz;

const getBaz = (bar) => (bar ? bar.baz : baz);
const foo = getBaz(getBar());

const foo = ((bar) => {
  return bar ? bar.baz : baz;
})(getBar());
```