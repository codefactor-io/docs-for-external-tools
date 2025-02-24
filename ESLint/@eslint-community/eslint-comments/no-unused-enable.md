Pattern: Ineffective `eslint-enable` comment

Issue: -

## Description

`eslint-enable` comments that don't correspond to any active rule disables are unnecessary and can lead to confusion. Each enable directive should have a matching disable directive.

## Examples

Example of **incorrect** code:
```javascript
/*eslint-disable no-undef */
doSomething()
/*eslint-enable no-undef-init */

// Or enabling with nothing disabled
doSomething()
/*eslint-enable */
```

Example of **correct** code:
```javascript
/*eslint-disable no-undef */
doSomething()
/*eslint-enable no-undef */

// No unnecessary enable comments
doSomething()
```