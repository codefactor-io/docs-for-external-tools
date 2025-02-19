Pattern: Use of CommonJS module

Issue: -

## Description

Modern JavaScript codebases use ES modules (`import`/`export`) instead of CommonJS syntax (`require`, `module.exports`, `exports.*`). Using CommonJS syntax in an ES module codebase reduces consistency and maintainability.

## Examples

Example of **incorrect** code:
```javascript
var mod = require("fs");
module.exports = "Hello";
exports.sayHello = function() {
  return "Hello";
};
```

Example of **correct** code:
```javascript
import fs from "fs";
export const sayHello = () => "Hello";
export default "Hello";
```