Pattern: Commented out test

Issue: -

## Description

Tests that are commented out may be forgotten and never uncommented. If a test is temporarily unnecessary, use `.skip()` or remove it entirely.

## Examples

Example of **incorrect** code:
```javascript
// describe('foo', () => {});
// it('foo', () => {});
// test('foo', () => {});
// test.skip('foo', () => {});
```

Example of **correct** code:
```javascript
describe('foo', () => {});
test.skip('foo', () => {});
it('foo', () => {});
```