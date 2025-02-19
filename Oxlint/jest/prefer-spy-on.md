Pattern: Property mock assignment

Issue: -

## Description

Assigning mock functions directly to properties makes cleanup harder as the original implementation must be manually restored. Using `jest.spyOn()` allows for automatic cleanup through Jest's built-in restoration methods.

## Examples

Example of **incorrect** code:
```javascript
Date.now = jest.fn();
obj.method = jest.fn(() => 42);
```

Example of **correct** code:
```javascript
jest.spyOn(Date, "now");
jest.spyOn(obj, "method").mockImplementation(() => 42);
```