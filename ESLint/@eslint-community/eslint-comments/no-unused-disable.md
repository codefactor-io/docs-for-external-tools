Pattern: Unnecessary rule disable

Issue: -

## Description

Unused `eslint-disable` comments may accumulate over time as code is refactored or bugs are fixed. These unnecessary comments should be removed to prevent overlooking real ESLint warnings in the future.

## Examples

Example of **incorrect** code:
```javascript
// With rules: eqeqeq: error, no-undef: error
var foo = bar() //eslint-disable-line no-undef,eqeqeq
// The eqeqeq rule isn't violated here

// With no actual violations
doSomething() //eslint-disable-line
```

Example of **correct** code:
```javascript
// With rules: eqeqeq: error, no-undef: error
var foo = bar() //eslint-disable-line no-undef
// Only disabling rules that are actually violated

// Or with no directives when not needed
doSomething()
```