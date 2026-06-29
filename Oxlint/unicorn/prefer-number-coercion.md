Pattern: Use of parsing function for number coercion

Issue: -

## Description

`parseFloat()` and `parseInt()` parse numeric prefixes and ignore trailing text.
`Number()` parses the full input, which better matches intent when coercing values.

## Examples

Example of **incorrect** code:
```javascript
const value = parseFloat(input);
const integer = parseInt(input, 10);
```

Example of **correct** code:
```javascript
const value = Number(input);
const integer = Math.trunc(Number(input));
```
