Pattern: Deprecated test prefix

Issue: -

## Description

Jest provides two ways to mark tests as focused or skipped: prefixes (f/x) and method modifiers (.only/.skip). Using .only and .skip is preferred for better readability and consistency.

## Examples

Example of **incorrect** code:
```javascript
fit("focused test", () => {});
xit("skipped test", () => {});
fdescribe("focused suite", () => {});
xdescribe("skipped suite", () => {});
```

Example of **correct** code:
```javascript
test.only("focused test", () => {});
test.skip("skipped test", () => {});
describe.only("focused suite", () => {});
describe.skip("skipped suite", () => {});
```