Pattern: Ambiguous module syntax

Issue: -

## Description

This rule warns if a `module` could be mistakenly parsed as a `script` by a consumer leveraging Unambiguous JavaScript Grammar to determine the correct parsing goal.

The rule will respect the `parserOptions.sourceType` from ESLint config, meaning files explicitly parsed as `script` per that setting will not be reported.

This plugin uses Unambiguous JavaScript Grammar internally to decide whether dependencies should be parsed as modules and searched for exports matching the imported names, so it may be beneficial to keep this rule on even if your application will run in an explicit module-only environment.

## Examples

Example of **correct** code for files parsed as `module` by ESLint:
```js
import 'foo'
function x() {
  return 42
}
```

```js
export function x() {
  return 42
}
```

```js
;(function x() {
  return 42
})()
export {} // Simple way to mark side-effects-only file as 'module' without any imports/exports
```

Example of **incorrect** code:
```js
;(function x() {
  return 42
})()
```