Pattern: Misplaced import

Issue: -

## Description

Import statements should be grouped together at the top of the file. Since imports are hoisted, imported modules are evaluated before any interspersed statements, which can lead to unexpected behavior when imports are scattered throughout the file.

## Examples

Example of **incorrect** code:
```javascript
import { x } from "./foo";
export { x };
import { y } from "./bar"; // Import after non-import statement
```

Example of **correct** code:
```javascript
import { x } from "./foo";
import { y } from "./bar";
export { x, y };
```