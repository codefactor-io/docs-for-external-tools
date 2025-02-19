Pattern: Duplicate key in object literal

Issue: -

## Description

Multiple properties with the same key in object literals cause the last instance to silently overwrite previous ones. This often indicates a copy-paste error or typo and can lead to unexpected behavior.

## Examples

Example of **incorrect** code:
```javascript
var foo = {
  bar: "baz",
  bar: "qux"  // Overwrites previous bar
};

const config = {
  name: "project",
  version: "1.0.0",
  name: "test"  // Overwrites previous name
};

var obj = {
  0x1: "baz",
  1: "qux"    // Same as 0x1 in decimal
};
```

Example of **correct** code:
```javascript
var foo = {
  bar: "baz",
  qux: "qux"
};

const config = {
  name: "project",
  version: "1.0.0",
  code: "test"
};
```