Pattern: Use of test hook

Issue: -

## Description

Jest provides global functions for setup and teardown tasks, which are
called before/after each test case and each test suite. The use of these
hooks promotes shared state between tests.

This rule reports for the following function calls:

* `beforeAll`
* `beforeEach`
* `afterAll`
* `afterEach`

## Examples

Example of **incorrect** code:
```javascript
function setupFoo(options) {
  /* ... */
}
function setupBar(options) {
  /* ... */
}

describe("foo", () => {
  let foo;
  beforeEach(() => {
    foo = setupFoo();
  });
  afterEach(() => {
    foo = null;
  });
  it("does something", () => {
    expect(foo.doesSomething()).toBe(true);
  });
  describe("with bar", () => {
    let bar;
    beforeEach(() => {
      bar = setupBar();
    });
    afterEach(() => {
      bar = null;
    });
    it("does something with bar", () => {
      expect(foo.doesSomething(bar)).toBe(true);
    });
  });
});
```
