Pattern: Inconsistent index existence check

Issue: -

## Description

When checking for element existence using methods like `indexOf()`, `lastIndexOf()`, `findIndex()`, and `findLastIndex()`, use strict equality comparisons with `-1` for consistency and clarity.

## Examples

Example of **incorrect** code:
```javascript
const index = foo.indexOf("bar");
if (index < 0) {}

const index = foo.indexOf("bar");
if (index >= 0) {}
```

Example of **correct** code:
```javascript
const index = foo.indexOf("bar");
if (index === -1) {}

const index = foo.indexOf("bar");
if (index !== -1) {}
```