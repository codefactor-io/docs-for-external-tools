Pattern: Unused error parameter in catch clause

Issue: -

## Description

When a `catch` block doesn't use the error parameter, it can be omitted for cleaner code. Modern JavaScript allows catch clauses without binding parameters.

## Examples

Example of **incorrect** code:
```javascript
try {
  // ...
} catch (e) {}
```

Example of **correct** code:
```javascript
try {
  // ...
} catch {}
```