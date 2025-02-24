Pattern: Empty `eslint-disable` comment

Issue: -

## Description

Using `eslint-disable` without specifying rule names disables all rules, which can lead to overlooking ESLint warnings unintentionally. Always specify the exact rules to disable.

## Examples

Example of **incorrect** code:
```javascript
var foo; //eslint-disable-line
```

Example of **correct** code:
```javascript
var foo; //eslint-disable-line no-unused-vars
```