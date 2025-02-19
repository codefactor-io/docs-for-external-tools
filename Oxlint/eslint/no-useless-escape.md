Pattern: Unnecessary character escape

Issue: -

## Description

Escaping characters that don't need to be escaped in strings or regular expressions makes code harder to read and maintain. Only characters that have special meaning in the current context need to be escaped.

## Examples

Example of **incorrect** code:
```javascript
let str = "\'";  // Single quote in double-quoted string
let str2 = '\"';  // Double quote in single-quoted string
const special = '\#';  // Hash doesn't need escaping
let template = `\"`; // Quote in template literal
const regex = /\!/;  // Exclamation mark in regex
const range = /[a\-z]/;  // Hyphen not at start/end of class
```

Example of **correct** code:
```javascript
let str = "'";  // No escape needed
let str2 = '"';  // No escape needed
const special = '#';  // No escape needed
let template = '`';  // Quote in different string type
const regex = /[[\]]/;  // Brackets need escaping in class
const range = /[a-z]/;  // Hyphen as range operator
const escapes = "\\n\\t";  // Valid control characters
```