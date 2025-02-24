Pattern: Disabling restricted ESLint rule

Issue: -

## Description

This rule prevents disabling specific ESLint rules that are configured as restricted. This ensures important rules cannot be bypassed with disable comments.

## Examples

Example of **incorrect** code:
```javascript
// With configuration: [error, no-undef, no-unused-vars]
/*eslint-disable no-undef */
f()

f() //eslint-disable-line no-undef

f() //eslint-disable-line
```

Example of **correct** code:
```javascript
// With configuration: [error, no-undef, no-unused-vars]
f() //eslint-disable-line another-rule
```