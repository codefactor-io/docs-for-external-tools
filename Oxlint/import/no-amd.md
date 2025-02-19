Pattern: Use of AMD module

Issue: -

## Description

AMD (Asynchronous Module Definition) is an older module format that adds unnecessary complexity and is considered outdated. Modern JavaScript development favors ES6 modules and CommonJS in Node.js for better maintainability and consistency.

## Examples

Example of **incorrect** code:
```javascript
require([a, b], function () {});
```

Example of **correct** code:
```javascript
require("../name");
require(`../name`);
```