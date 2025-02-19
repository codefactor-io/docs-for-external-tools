Pattern: Skipping multiple array elements in destructuring

Issue: -

## Description

While array destructuring is useful, skipping consecutive elements with empty slots makes code harder to read and understand. Consider using array methods or explicit indexing for clearer intent.

## Examples

Example of **incorrect** code:
```javascript
const [, , foo] = parts;
```

Example of **correct** code:
```javascript
const [foo] = parts;
```