Pattern: Missing mock type parameter

Issue: -

## Description

When using `vi.fn()` to mock functions, by default, the mocked function has the type of `(...args: any[]) => any`. To add more specific types to the mocked function, a type parameter needs to be added to the call, e.g. `vi.fn<(arg1: string, arg2: boolean) => number>()`.

Additionally, there are two more mock functions with type parameters that cannot be automatically inferred by the TypeScript compiler, `vi.importActual` and `vi.importMock`. This rule doesn't by default report these function, however, the check can be enabled by setting the `checkImportFunctions` rule option.

## Examples

Example of **incorrect** code:

```ts
import { vi } from 'vitest'

test('foo', () => {
  const myMockedFn = vi.fn()
})
```

Example of **correct** code:

```ts
import { vi } from 'vitest'

test('foo', () => {
  const myMockedFnOne = vi.fn<(arg1: string, arg2: boolean) => number>()
  const myMockedFnTwo = vi.fn<() => void>()
  const myMockedFnThree = vi.fn<any>()
})
```