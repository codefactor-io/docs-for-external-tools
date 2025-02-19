Pattern: Equality comparison as boolean

Issue: -

## Description

Using boolean assertions for equality comparisons is less readable than Jest's built-in equality matchers. The matchers provide clearer error messages when tests fail.

## Examples

Example of **incorrect** code:
```javascript
expect(x === 5).toBe(true);
expect(name === "Carl").not.toEqual(true);
expect(obj !== otherObj).toStrictEqual(true);
```

Example of **correct** code:
```javascript
expect(x).toBe(5);
expect(name).not.toEqual("Carl");
expect(obj).not.toStrictEqual(otherObj);
```