Pattern: Use of Jest method alias

Issue: -

## Description

Using aliased method names instead of their canonical names reduces code consistency and makes searching for method usage more difficult. These aliases will be removed in future Jest versions.

## Examples

Example of **incorrect** code:
```javascript
expect(fn).toBeCalled();
expect(fn).toBeCalledWith();
expect(fn).toReturn();
expect(fn).toThrowError();
```

Example of **correct** code:
```javascript
expect(fn).toHaveBeenCalled();
expect(fn).toHaveBeenCalledWith();
expect(fn).toHaveReturned();
expect(fn).toThrow();
```