Pattern: Duplicate import

Issue: -

## Description

Importing the same module multiple times creates unnecessary redundancy and complexity. Multiple import statements for the same module should be combined into a single import statement where possible.

## Examples

Example of **incorrect** code:
```javascript
import { foo } from "./module";
import { bar } from "./module";

import a from "./module";
import { b } from "./module";
```

Example of **correct** code:
```javascript
import { foo, bar } from "./module";
import defaultExport, { namedExport } from "./module";
```