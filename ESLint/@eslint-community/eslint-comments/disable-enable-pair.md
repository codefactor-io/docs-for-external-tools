Pattern: Missing `eslint-enable` comment

Issue: -

## Description

Each `eslint-disable` directive needs a corresponding `eslint-enable` directive to ensure ESLint rules are not accidentally disabled for the entire file. Missing enable comments can cause warnings to be overlooked.

## Examples

Example of **incorrect** code:
```javascript
/*eslint-disable no-undef, no-unused-vars */
var foo = bar()

// Partial enable is also incorrect
/*eslint-disable no-undef, no-unused-vars */
var foo = bar()
/*eslint-enable no-unused-vars */
```

Example of **correct** code:
```javascript
/*eslint-disable no-undef, no-unused-vars */
var foo = bar()
/*eslint-enable no-undef, no-unused-vars */

// Or enable all at once
/*eslint-disable no-undef, no-unused-vars */
var foo = bar()
/*eslint-enable*/
```