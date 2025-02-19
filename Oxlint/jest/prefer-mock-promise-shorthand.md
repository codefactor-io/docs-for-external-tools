Pattern: Verbose promise mock

Issue: -

## Description

Jest provides shorthand methods for mocking promise-returning functions. Using `mockResolvedValue()` or `mockRejectedValue()` is clearer and more concise than `mockImplementation()` with Promise construction.

## Examples

Example of **incorrect** code:
```javascript
jest.fn().mockImplementation(() => Promise.resolve(42));
mock.mockReturnValue(Promise.reject(new Error()));
```

Example of **correct** code:
```javascript
jest.fn().mockResolvedValue(42);
mock.mockRejectedValue(new Error());
```