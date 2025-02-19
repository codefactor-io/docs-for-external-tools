Pattern: Type assertion for mock

Issue: -

## Description

Using type assertions with Jest's mock types (jest.Mock, jest.MockedFunction, etc.) is less type-safe than using the `jest.mocked()` helper function, which properly preserves type information.

## Examples

Example of **incorrect** code:
```typescript
(foo as jest.Mock).mockReturnValue(1);
const mock = (someFunction as jest.Mock).mockReturnValue(true);
(obj.method as unknown as jest.Mock).mockReturnValue("value");
```

Example of **correct** code:
```typescript
jest.mocked(foo).mockReturnValue(1);
const mock = jest.mocked(someFunction).mockReturnValue(true);
jest.mocked(obj.method).mockReturnValue("value");
```