Pattern: Unnecessary ternary expression

Issue: -

## Description

Using ternary operators to return boolean values or to provide fallbacks when simpler alternatives exist makes code unnecessarily complex. Boolean expressions and logical OR operators can often replace these ternaries with more readable code.

## Examples

Example of **incorrect** code:
```js
const isYes = answer === 1 ? true : false;
const isNo = answer === 1 ? false : true;

foo(bar ? bar : 1);
```

Example of **correct** code:
```js
const isYes = answer === 1;
const isNo = answer !== 1;

foo(bar || 1);
```