Pattern: Meaningless file content

Issue: -

## Description

Files containing only whitespace, comments, directives, empty statements, empty blocks, or hashbang clutter the codebase without providing any functional value.

## Examples

Example of **incorrect** code:
```javascript
// Only a comment
   
/* Multi-line
   comment */

{}

;
```

Example of **correct** code:
```javascript
// A comment followed by actual code
const value = 42;

/* Multi-line comment */
function doSomething() {
  // Implementation
}
```