Pattern: Ambiguous module type

Issue: -

## Description

A file that could be parsed as either a script or an ESM module creates ambiguity in ESM-only environments. Files should be clearly identifiable as ESM modules through imports, exports, or explicit markers.

## Examples

Example of **incorrect** code:
```javascript
function x() {}

(function x() {
  return 42;
})();
```

Example of **correct** code:
```javascript
import "foo";
export function x() {
  return 42;
}

// Or mark as module without imports/exports
(function x() {
  return 42;
})();
export {};
```