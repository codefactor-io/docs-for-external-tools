Pattern: Inconsistent numeric literal case

Issue: -

## Description

Using lowercase letters in numeric literals makes them harder to differentiate from identifiers. Hexadecimal, binary, and octal literals should use uppercase letters for better readability.

## Examples

Example of **incorrect** code:
```javascript
const foo = 0xff;
const foo = 0xffn;
const foo = 0b10;
const foo = 0o76;
const foo = 2e-5;
```

Example of **correct** code:
```javascript
const foo = 0xFF;
const foo = 0xFFn;
const foo = 0b10;
const foo = 0o76;
const foo = 2E5;
```