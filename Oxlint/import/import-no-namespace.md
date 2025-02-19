Pattern: Namespace import

Issue: -

## Description

Namespace imports (using `*`) import the entire module into a single namespace, even when only specific functions or classes are needed. This leads to:
- Potential naming conflicts when different modules have similar names
- Namespace pollution with unnecessary functions and variables
- Reduced code clarity and harder refactoring
- Less efficient tree-shaking, resulting in larger bundle sizes

## Examples

Example of **incorrect** code:
```javascript
import * as user from "user-lib";
import some, * as user from "./user";
```

Example of **correct** code:
```javascript
import { getUserName, isUser } from "user-lib";
import user from "user-lib";
import defaultExport, { isUser } from "./user";
```