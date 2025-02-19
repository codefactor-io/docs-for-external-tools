Pattern: Empty object fallback in spread operator

Issue: -

## Description

Using an empty object as a fallback when spreading falsy values is unnecessary since spreading falsy values in object literals won't add any properties.

## Examples

Example of **incorrect** code:
```javascript
const object = { ...(foo || {}) };
```

Example of **correct** code:
```javascript
const object = { ...foo };
const object = { ...(foo || { not: "empty" }) };
```