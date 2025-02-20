Pattern: Unnecessary ternary expression

Issue: -

## Description

Using logical operators (`||`, `??`) can provide shorter and simpler alternatives to ternary expressions when checking for fallback values.

## Examples

Example of **incorrect** code:
```javascript
const foo = bar ? bar : baz;
console.log(foo ? foo : bar);
```

Example of **correct** code:
```javascript
const foo = bar || baz;
console.log(foo ?? bar);
```