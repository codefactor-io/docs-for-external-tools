Pattern: Dynamic module path

Issue: -

## Description

Using expressions that are resolved at runtime in import statements makes it difficult to determine the module source and hinders static analysis tools. Module paths should be static strings for better code navigation and optimization.

## Examples

Example of **incorrect** code:
```javascript
require(name);
require(`../${name}`);
```

Example of **correct** code:
```javascript
require("../name");
require(`../name`);
```