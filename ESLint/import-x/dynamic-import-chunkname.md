Pattern: Missing or invalid webpack chunk name

Issue: -

## Description

This rule reports any dynamic imports without a properly formatted webpackChunkName specified in a leading block comment. When you don't explicitly name chunks, webpack will autogenerate chunk names that are not consistent across builds, which prevents long-term browser caching.

The rule enforces naming of webpack chunks in dynamic imports to ensure consistent chunk names across builds.

## Examples

Example of **incorrect** code:
```javascript
// no leading comment
import('someModule')

// incorrectly formatted comment
import(
  /*webpackChunkName:"someModule"*/
  'someModule'
)
import(
  /* webpackChunkName : "someModule" */
  'someModule'
)

// invalid syntax for webpack comment
import(
  /* totally not webpackChunkName: "someModule" */
  'someModule'
)

// single-line comment, not a block-style comment
import(
  // webpackChunkName: "someModule"
  'someModule'
)

// chunk names are disallowed when eager mode is set
import(
  /* webpackMode: "eager" */
  /* webpackChunkName: "someModule" */
  'someModule'
)
```

Example of **correct** code:
```javascript
import(
  /* webpackChunkName: "someModule" */
  'someModule'
)
import(
  /* webpackChunkName: "someOtherModule12345789" */
  'someModule'
)
import(
  /* webpackChunkName: "someModule" */
  /* webpackPrefetch: true */
  'someModule'
)
import(
  /* webpackChunkName: "someModule", webpackPrefetch: true */
  'someModule'
)

// using single quotes instead of double quotes
import(
  /* webpackChunkName: 'someModule' */
  'someModule'
)
```