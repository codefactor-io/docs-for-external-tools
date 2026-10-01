Pattern: Generic equality matcher for primitive literal

Issue: -

## Description

When asserting against primitive literals such as numbers and strings,
the equality matchers all operate the same, but read slightly
differently in code.

This rule recommends using the `toBe` matcher in these situations, as
it forms the most grammatically natural sentence. For `null`,
`undefined`, and `NaN` this rule recommends using their specific `toBe`
matchers, as they give better error messages as well.

## Examples

Example of **incorrect** code:
```javascript
expect(value).not.toEqual(5);
expect(getMessage()).toStrictEqual("hello world");
expect(loadMessage()).resolves.toEqual("hello world");
```

Example of **correct** code:
```javascript
expect(value).not.toBe(5);
expect(getMessage()).toBe("hello world");
expect(loadMessage()).resolves.toBe("hello world");
expect(didError).not.toBe(true);
expect(catchError()).toStrictEqual({ message: "oh noes!" });
```
