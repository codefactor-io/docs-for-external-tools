Pattern: Hexadecimal escape sequence in string

Issue: -

## Description

Using hexadecimal escape sequences (`\x`) makes code less consistent and harder to understand. Unicode escapes (`\u`) should be used instead for better clarity and consistency.

## Examples

Example of **incorrect** code:
```javascript
const foo = "\x1B";
const foo = `\x1B${bar}`;
```

Example of **correct** code:
```javascript
const foo = "\u001B";
const foo = `\u001B${bar}`;
```