Pattern: Duplicate export

Issue: -

## Description

Having multiple exports of the same name creates ambiguity in the codebase and can lead to runtime errors. This happens when directly exporting the same name multiple times or when export conflicts occur through re-exports from other modules.

## Examples

Example of **incorrect** code:
```javascript
let foo;
export { foo };
export * from "./export-all"; // Potential conflict if export-all.js exports foo
```

Example of **correct** code:
```javascript
let foo;
export { foo as foo1 }; // Renamed to avoid conflict
export * from "./export-all";
```