Pattern: Single `eslint-enable` for multiple disable comments

Issue: -

## Description

Using a single `eslint-enable` comment to re-enable rules from multiple `eslint-disable` comments can unintentionally enable rules. Each disable comment should have its own corresponding enable comment.

## Examples

Example of **incorrect** code:
```javascript
/*eslint-disable no-undef */
f()
/*eslint-disable no-var */
var a
/*eslint-enable */

// Or specifying multiple rules at once
/*eslint-disable no-undef */
f()
/*eslint-disable no-var */
var a
/*eslint-enable no-undef, no-var */
```

Example of **correct** code:
```javascript
/*eslint-disable no-undef */
f()
/*eslint-disable no-var */
var a
/*eslint-enable no-var */

/*eslint-enable no-undef */
```