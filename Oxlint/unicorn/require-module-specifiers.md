Pattern: Empty import or export specifier list

Issue: -

## Description

Empty `import`/`export` specifiers add no value and can be confusing.
If you want to import a module for side effects, use `import 'module'` instead.

## Examples

Example of **incorrect** code:
```javascript
import {} from "foo";
import foo from "foo";
export {} from "foo";
export {};
```

Example of **correct** code:
```javascript
import "foo";
import foo from "foo";
```
