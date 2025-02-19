Pattern: Generic mock call assertion

Issue: -

## Description

Using `toBeCalled()` or `toHaveBeenCalled()` without specifying arguments makes test intentions unclear. Use `toBeCalledWith()` or `toHaveBeenCalledWith()` to explicitly verify the arguments passed to mocks.

## Examples

Example of **incorrect** code:
```javascript
expect(mockFunction).toBeCalled();
expect(mockFunction).toHaveBeenCalled();
```

Example of **correct** code:
```javascript
expect(mockFunction).toBeCalledWith(expectedArg);
expect(mockFunction).toBeCalledWith(expect.any(String));
expect(mockFunction).toBeCalledTimes(1);
```