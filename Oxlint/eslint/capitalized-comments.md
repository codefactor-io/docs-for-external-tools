Pattern: Inconsistent comment capitalization

Issue: -

## Description

Inconsistent capitalization of comments can make code harder to read.
This rule helps enforce a consistent style across the codebase.

## Examples

Example of **incorrect** code with the default `"always"` option:
```javascript
// lowercase comment
/* lowercase block comment */
```

Example of **correct** code with the default `"always"` option:
```javascript
// Capitalized comment
/* Capitalized block comment */
// 123 - comments starting with non-letters are ignored
```
