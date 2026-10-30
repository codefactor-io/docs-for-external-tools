Pattern: Inconsistent type specifier style

Issue: -

## Description

Mixing top-level `import type { Foo } from 'foo'` with inline `{ type Bar }`
forces readers to mentally switch contexts when scanning your imports.
Enforcing one style makes it immediately obvious which imports are types and which are value imports.

## Examples

Example of **incorrect** code:
```typescript
import { type Foo } from "Foo";
import Foo, { type Bar } from "Foo";
```

Example of **correct** code:
```typescript
import type { Foo } from 'Foo';
import type Foo, { Bar } from 'Foo';
```
