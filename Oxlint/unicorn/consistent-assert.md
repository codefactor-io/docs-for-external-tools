Pattern: Direct assertion function call

Issue: -

## Description

Using `assert()` directly is less explicit than using `assert.ok()`. The latter more clearly indicates the intent to check if a value is truthy and maintains a consistent style with other assertion methods, improving code readability and maintainability.

## Examples

Example of **incorrect** code:
```javascript
import assert from 'node:assert/strict';

assert(divide(10, 2) === 5);
```

Example of **correct** code:
```javascript
import assert from 'node:assert/strict';

assert.ok(divide(10, 2) === 5);
assert.strictEqual(actual, expected);
assert.deepStrictEqual(actual, expected);
```