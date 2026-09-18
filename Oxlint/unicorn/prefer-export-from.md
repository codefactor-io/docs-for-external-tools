Pattern: Indirect re-export

Issue: -

## Description

Separating re-exports into import and export statements is discouraged because it
unnecessarily pollutes the current module's scope and adds redundant boilerplate code.

## Examples

Example of **incorrect** code:
```javascript
import defaultExport from "./foo.js";
export default defaultExport;

import { named } from "./foo.js";
export { named };
```

Example of **correct** code:
```javascript
export { default } from "./foo.js";

export { named } from "./foo.js";
```
