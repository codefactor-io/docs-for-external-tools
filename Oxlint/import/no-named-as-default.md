Pattern: Named export as default import name

Issue: -

## Description

Using a named export's identifier for importing a default export creates confusion and makes it harder to understand which value is being imported. This occurs when an imported default export is assigned the same name as a named export from the same module.

## Examples

Example of **incorrect** code:
```javascript
// foo.js
export default "foo";
export const bar = "baz";

// main.js
import bar from "./foo.js";  // bar is already a named export
```

Example of **correct** code:
```javascript
// foo.js
export default "foo";
export const bar = "baz";

// main.js
import foo from "./foo.js";  // Using different name for default import
```