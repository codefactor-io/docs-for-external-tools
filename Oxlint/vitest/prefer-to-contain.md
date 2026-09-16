Pattern: Inclusion check with generic matcher

Issue: -

## Description

This rule triggers a warning if `toBe()`, `toEqual()` or `toStrictEqual()` is
used to assert object inclusion in an array

## Examples

Example of **incorrect** code:
```javascript
expect(a.includes(b)).toBe(true);
expect(a.includes(b)).not.toBe(true);
expect(a.includes(b)).toBe(false);
expect(a.includes(b)).toEqual(true);
expect(a.includes(b)).toStrictEqual(true);
```

Example of **correct** code:
```javascript
expect(a).toContain(b);
expect(a).not.toContain(b);
```
