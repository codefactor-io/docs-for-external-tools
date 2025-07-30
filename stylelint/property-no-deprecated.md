Pattern: Deprecated property

Issue: -

## Description

```css
  a { word-wrap: break-word; }
/**      ↑
 * Deprecated property */
```

This rule flags properties that were removed or deprecated after being in the CSS specifications, including editor drafts, and were either:

- shipped in a stable version of a browser
- shipped by a developer channel/edition browser
- shipped but behind experimental flags
- polyfilled with some adoption before any browser actually shipped
- had an MDN page at one point in time

## Examples

The following patterns are considered problems:

<!-- prettier-ignore -->
```css
a { clip: rect(0, 0, 0, 0); }
```

<!-- prettier-ignore -->
```css
a { word-wrap: break-word; }
```

The following patterns are _not_ considered problems:

<!-- prettier-ignore -->
```css
a { clip-path: rect(0, 0, 0, 0); }
```

<!-- prettier-ignore -->
```css
a { overflow-wrap: break-word; }
```