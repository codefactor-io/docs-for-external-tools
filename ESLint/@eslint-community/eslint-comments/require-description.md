Pattern: Missing description in ESLint directive comment

Issue: -

## Description

ESLint directive comments should include explanatory descriptions to document why the directive is necessary. This helps other developers understand the reasoning behind disabling or configuring rules.

## Examples

Example of **incorrect** code:
```javascript
/* eslint no-undef: off */
/* eslint-env browser */
/* eslint-disable eqeqeq */
// eslint-disable-next-line
/* global $ */
```

Example of **correct** code:
```javascript
/* eslint no-undef: off -- Here's a description about why this directive-comment is necessary. */
/* eslint-env browser -- This script works in browser. */
// eslint-disable-next-line -- Temporarily avoids the lint error problem. See issue XXX.
/* global $ -- This script using jQuery. */
```