Pattern: Excessive describe nesting

Issue: -

## Description

Deeply nested describe blocks make test suites harder to read and understand. Keep nesting to a reasonable depth to maintain test clarity and structure.

## Examples

Example of **incorrect** code:
```javascript
describe("foo", () => {
  describe("bar", () => {
    describe("baz", () => {
      describe("qux", () => {
        describe("quxx", () => {
          describe("too deep", () => {
            it("should work", () => {
              expect(value).toBe(true);
            });
          });
        });
      });
    });
  });
});
```

Example of **correct** code:
```javascript
describe("foo", () => {
  describe("bar", () => {
    describe("baz", () => {
      it("should work", () => {
        expect(value).toBe(true);
      });
    });
  });
});
```