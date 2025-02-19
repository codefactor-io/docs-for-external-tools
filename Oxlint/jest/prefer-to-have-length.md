Pattern: Direct length comparison

Issue: -

## Description

Using `toBe()` or `toEqual()` to check length properties provides less readable error messages. The `toHaveLength()` matcher is specifically designed for checking array and string lengths with clearer failure output.

## Examples

Example of **incorrect** code:
```javascript
expect(array.length).toBe(2);
expect(string.length).toEqual(5);
expect(list["length"]).toBe(0);
```

Example of **correct** code:
```javascript
expect(array).toHaveLength(2);
expect(string).toHaveLength(5);
expect(list).toHaveLength(0);
```