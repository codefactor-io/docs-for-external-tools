Pattern: Use of deprecated Jest function

Issue: -

## Description

Some Jest functions have been renamed or replaced with more powerful APIs. Using deprecated functions makes code harder to maintain and may break in future Jest versions.

## Examples

Example of **incorrect** code:
```javascript
jest.resetModuleRegistry();
jest.addMatchers();
jest.runTimersToTime(1000);
jest.genMockFromModule("./module");
```

Example of **correct** code:
```javascript
jest.resetModules();
expect.extend();
jest.advanceTimersByTime(1000);
jest.createMockFromModule("./module");
```