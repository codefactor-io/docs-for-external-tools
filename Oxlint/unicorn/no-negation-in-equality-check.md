Pattern: Negation on left side of equality check

Issue: -

## Description

Putting a negation operator on the left side of an equality check is likely a mistake from trying to negate the entire condition. Use the appropriate comparison operator or negate the entire expression instead.

## Examples

Example of **incorrect** code:
```javascript
if (!foo === bar) {}
if (!foo !== bar) {}
```

Example of **correct** code:
```javascript
if (foo !== bar) {}
if (!(foo === bar)) {}
```