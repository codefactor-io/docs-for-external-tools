Pattern: Inconsistent test declaration

Issue: -

## Description

It's a good practice to be consistent in your test suite, so that all tests are written in the same way.

## Examples

Example of **incorrect** code:
```javascript
it("foo");
it.only("foo");
```

Example of **correct** code:
```javascript
test("foo");
test.only("foo");
```
