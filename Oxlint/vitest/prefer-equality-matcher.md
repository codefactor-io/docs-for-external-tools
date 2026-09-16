Pattern: Equality expression with generic matcher

Issue: -

## Description

Testing equality expressions with generic matchers like `toBe(true)`
makes tests harder to read and understand. When tests fail, the error
messages are less helpful because they don't show what the actual values
were. Using specific equality matchers provides clearer test intent and
better debugging information.

## Examples

Example of **incorrect** code:
```javascript
expect(x === 5).toBe(true);
expect(name === "Carl").not.toEqual(true);
expect(myObj !== thatObj).toStrictEqual(true);
```

Example of **correct** code:
```javascript
expect(x).toBe(5);
expect(name).not.toEqual("Carl");
expect(myObj).toStrictEqual(thatObj);
```
