Pattern: Named default import

Issue: -

## Description

Using named import syntax for default exports (`import { default as foo }`) is unnecessarily verbose when a simpler default import syntax (`import foo`) exists for this purpose.

## Examples

Example of **incorrect** code:
```javascript
import { default as foo } from "./foo.js";
import { default as foo, bar } from "./foo.js";
```

Example of **correct** code:
```javascript
import foo from "./foo.js";
import foo, { bar } from "./foo.js";
```