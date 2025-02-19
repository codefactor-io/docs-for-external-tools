Pattern: Use of loose equality

Issue: -

## Description

Using `toEqual()` performs a loose equality check that may miss differences in undefined properties and types. `toStrictEqual()` provides more thorough comparison and clearer failure messages.

## Examples

Example of **incorrect** code:
```javascript
expect(value).toEqual({ a: 1 });
expect(result).toEqual({ name: "test", type: undefined });
```

Example of **correct** code:
```javascript
expect(value).toStrictEqual({ a: 1 });
expect(result).toStrictEqual({ name: "test", type: undefined });
```