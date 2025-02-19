Pattern: Large barrel import/export

Issue: -

## Description

Barrel files using `export *` or `import *` that exceed the module threshold (default 100) can significantly impact build performance and bundle size. Use explicit exports instead.

## Examples

Example of **incorrect** code:
```javascript
// index.ts with >100 re-exported modules
export * from './components';
import * as Components from './components';
```

Example of **correct** code:
```javascript
// Explicit exports
export { Button, Card, Modal } from './components';
import { Button, Card, Modal } from './components';
```