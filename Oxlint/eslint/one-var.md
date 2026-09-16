Pattern: Separate variable declarations

Issue: -

## Description

Consistent declaration grouping makes variable lifetimes and initialization patterns easier
to scan. This rule can require one declaration per scope, one declarator per statement, or
grouping only consecutive declarations.

## Examples

Example of **incorrect** code:
```javascript
var foo = 1;
var bar = 2;
```

Example of **correct** code:
```javascript
var foo = 1,
  bar = 2;
```
