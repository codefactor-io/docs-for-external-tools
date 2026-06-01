Pattern: Inconsistent import style

Issue: -

## Description

Some modules are easier to read when imported in a consistent way. For example, utility modules often work better with named imports, while modules that expose one primary interface are clearer as default imports.

## Examples

Example of **incorrect** code:

```javascript
import util from "node:util";
```

Example of **correct** code:

```javascript
import { promisify } from "node:util";
```