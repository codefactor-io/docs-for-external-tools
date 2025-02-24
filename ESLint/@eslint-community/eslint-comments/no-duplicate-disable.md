Pattern: Duplicate `eslint-disable` comment

Issue: -

## Description

Using duplicate `eslint-disable` comments (a mix of wide-range and narrow-range directive comments) can cause warnings to be overlooked in the future. Each rule should only be disabled once in a given context.

## Examples

Example of **incorrect** code:
```javascript
/*eslint-disable no-undef */

var foo = bar() //eslint-disable-line no-undef
```

Example of **correct** code:
```javascript
/*eslint-disable no-undef */

var foo = bar()
```

```javascript
var foo = bar() //eslint-disable-line no-undef
```