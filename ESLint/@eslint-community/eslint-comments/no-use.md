Pattern: Use of ESLint directive comments

Issue: -

## Description

Overuse of ESLint directive comments may cause developers to overlook bugs or violate coding standards. This rule can be configured to disallow specific types of directive comments to maintain code quality.

## Examples

Example of **incorrect** code:
```javascript
/* eslint no-undef: off */
/* eslint-env browser */
/* eslint-disable foo */
/* eslint-enable bar */
// eslint-disable-line
// eslint-disable-next-line
/* exported foo */
/* global $ */
/* globals a, b, c */
```

Example of **correct** code:
```javascript
// With configuration: ["error", {"allow": ["eslint-disable-next-line"]}]
// eslint-disable-next-line no-undef
doSomething();
```