Pattern: Missing padding around test block

Issue: -

## Description

Inconsistent formatting of code can make the code more difficult to read
and follow. This rule helps ensure that test blocks are visually
separated from the rest of the code, making them easier to identify while
looking through test files.

## Examples

Example of **incorrect** code:
```javascript
const thing = 123;
test("foo", () => {});
test("bar", () => {});
```

```javascript
const thing = 123;
it("foo", () => {});
it("bar", () => {});
```

Example of **correct** code:
```javascript
const thing = 123;

test("foo", () => {});

test("bar", () => {});
```

```javascript
const thing = 123;

it("foo", () => {});

it("bar", () => {});
```
