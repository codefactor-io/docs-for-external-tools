Pattern: Length check with generic matcher

Issue: -

## Description

This rule triggers a warning if `toBe()`, `toEqual()` or `toStrictEqual()` is
used to assert objects length property.

## Examples

Example of **incorrect** code:
```javascript
expect(files["length"]).toBe(1);
expect(files["length"]).toBe(1);
expect(files["length"])["not"].toBe(1);
```

Example of **correct** code:
```javascript
expect(files).toHaveLength(1);
```
