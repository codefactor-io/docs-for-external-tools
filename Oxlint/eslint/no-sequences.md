Pattern: Use of comma operator

Issue: -

## Description

The comma operator evaluates each of its operands (from left to right)
and returns the value of the last operand. However, this frequently
obscures side effects, and its use is often an accident.

## Examples

Example of **incorrect** code:
```javascript
((foo = doSomething()), val);

(0, eval("doSomething();"));

// Arrow function body needs double parentheses
const fn = () => (doSomething(), val);

// with allowInParentheses: false
foo = (doSomething(), val);
```

Example of **correct** code:
```javascript
foo = (doSomething(), val);

(0, eval)("doSomething();");

// Single extra parentheses is enough for conditions
do {} while ((doSomething(), !!test));

for (i = 0, j = 10; i < j; i++, j--) {}

// Arrow function body needs double parentheses
const fn = () => (doSomething(), val);
```
