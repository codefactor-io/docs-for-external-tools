Pattern: String interpolation in snapshot

Issue: -

## Description

Using string interpolation in snapshots prevents them from being properly updated. Property matchers should be used instead to handle dynamic values in snapshots.

## Examples

Example of **incorrect** code:
```javascript
expect(value).toMatchInlineSnapshot(`
  Object {
    property: ${interpolated}
  }
`);

expect(error).toThrowErrorMatchingInlineSnapshot(`${message}`);
```

Example of **correct** code:
```javascript
expect(value).toMatchInlineSnapshot({
  property: expect.any(String)
}, `
  Object {
    property: Any<String>
  }
`);
```