Pattern: Extra space in empty braces

Issue: -

## Description

Empty braces should not contain extra spaces or newlines as they reduce code readability. Keep empty braces concise without any whitespace between them.

## Examples

Example of **incorrect** code:
```javascript
const obj = { };
class A { }
```

Example of **correct** code:
```javascript
const obj = {};
class A {}
```