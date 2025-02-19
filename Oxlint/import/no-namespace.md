Pattern: Use of namespace import

Issue: -

## Description

Namespace imports (using `*`) import an entire module even when only specific functions are needed. This can lead to naming conflicts, namespace pollution, reduced code clarity, and less efficient tree-shaking.

## Examples

Example of **incorrect** code:
```javascript
import * as user from "user-lib";
import some, * as user from "./user";
```

Example of **correct** code:
```javascript
import { getUserName, isUser } from "user-lib";
import defaultExport, { isUser } from "./user";
```