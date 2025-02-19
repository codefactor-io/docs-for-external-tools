Pattern: Includes with boolean assertion

Issue: -

## Description

Using `includes()` with boolean assertions provides less readable error messages. The `toContain()` matcher is specifically designed for checking array inclusion with clearer failure output.

## Examples

Example of **incorrect** code:
```javascript
expect(array.includes(value)).toBe(true);
expect(array.includes(value)).toEqual(true);
expect(array.includes(value)).toBe(false);
```

Example of **correct** code:
```javascript
expect(array).toContain(value);
expect(array).not.toContain(value);
```