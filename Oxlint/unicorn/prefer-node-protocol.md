Pattern: Missing `node:` protocol in builtin imports

Issue: -

## Description

When importing Node.js builtin modules, using the `node:` protocol prefix helps avoid ambiguity with similarly named local modules and makes the code's intent clearer.

## Examples

Example of **incorrect** code:
```javascript
import fs from "fs";
```

Example of **correct** code:
```javascript
import fs from "node:fs";
```