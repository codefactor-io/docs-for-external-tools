Pattern: Empty test case

Issue: -

## Description

Empty test cases or test cases without implementation should use `test.todo()` to make them more visible in test summaries and clearly indicate pending work.

## Examples

Example of **incorrect** code:
```javascript
test("future test");
test("empty test", () => {});
test.skip("skipped empty test", () => {});
```

Example of **correct** code:
```javascript
test.todo("future test");
test.todo("needs implementation");
```