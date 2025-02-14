Pattern: Deprecated keyword for property within declaration

Issue: -

## Description

Disallow deprecated keywords for properties within declarations.

```css
  a { color: ThreeDDarkShadow; }
/**     ↑         ↑
 * property and value pairs like these */
```

This rule flags keywords that were removed or deprecated after being in the CSS specifications, including editor drafts, and were subsequently either:

- shipped in a stable version of a browser
- shipped by a developer channel/edition browser
- shipped but behind experimental flags
- polyfilled with some adoption before any browser actually shipped
- had an MDN page at one point in time


## Examples

The following patterns are considered problems:

<!-- prettier-ignore -->
```css
a { overflow: overlay; }
```

<!-- prettier-ignore -->
```css
a { text-justify: distribute; }
```

The following patterns are _not_ considered problems:

<!-- prettier-ignore -->
```css
a { overflow: auto; }
```

<!-- prettier-ignore -->
```css
a { text-justify: inter-character; }
```