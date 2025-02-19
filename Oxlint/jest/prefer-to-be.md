Pattern: Inconsistent equality matcher

Issue: -

## Description

When asserting primitive values (numbers, strings, booleans), using `toBe()` creates more natural-reading tests than `toEqual()` or `toStrictEqual()`. For `null`, `undefined`, and `NaN`, specific matchers provide better error messages.

## Examples

Example of **incorrect** code:
```javascript
expect(count).toEqual(5);
expect(message).toStrictEqual("hello");
expect(value).toEqual(null);
```

Example of **correct** code:
```javascript
expect(count).toBe(5);
expect(message).toBe("hello");
expect(value).toBeNull();
```